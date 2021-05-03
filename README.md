# UTS_PC_GUI

## Nama  : Siti Khulasoh
## Kelas : TI.19.A2
## Nim   : 311910445
 ## UTS PENGOLAHAN CITRA MEMBUAT APLIKASI GUI
 
 ## - HISTOGRAM IMAGE
 
 1. pertama kita buka aplikasi matlab kemudian tulislah "guide" pada bagian 'Command Window' kemudian ENTER, kemudian klik browser untuk menyimpan folder lalu klik OK
![1](https://user-images.githubusercontent.com/56240533/116882948-3c5c2e00-ac4f-11eb-9172-1bc088c5f1e6.png)
2. Setelah itu buatlah "klik stastic text" untuk memberi nama judul/file ,kemudian klik kanan untuk mengatur inspectornya![2](https://user-images.githubusercontent.com/56240533/116883428-cb694600-ac4f-11eb-8472-f701dda52340.png).
3. kemudian klik "Push botton" untuk membuka image yang akan di tampilkan lalu klik kanan untuk mengatur inspectornya.
![3](https://user-images.githubusercontent.com/56240533/116883738-226f1b00-ac50-11eb-9d0d-d543b474238d.png)
4.  kemudian klik "edit text" untuk menunjukan tempat yang akan kita tmpilkan kemudian.
![4](https://user-images.githubusercontent.com/56240533/116885179-cb6a4580-ac51-11eb-87ed-4667f1316705.png)
5. kemudian klik "table" tiga kali dengan berurutan untuk menunjukn jumlah pikselnya
![5asli](https://user-images.githubusercontent.com/56240533/116884218-afb26f80-ac50-11eb-8b67-cc6ef86f476b.png)
6. setelah itu tambahkan tiga axes dan berpasangan dengan table tersebut, setelah semuanya sudah dibuat, kemudian "save" lalu klik kanan pada bagian browse image setelah klik "vew callback" dan "callback" untuk menmpatkan source kodenya
![6](https://user-images.githubusercontent.com/56240533/116884590-19cb1480-ac51-11eb-9491-e2eefcecef69.png)
_contoh source kodenya
![7](https://user-images.githubusercontent.com/56240533/116884692-38c9a680-ac51-11eb-8868-f73f850696a8.png)
7. kemudian sudah terbuat lalu kita atur gambarnya dengan mengklik "browse image" dan pilih immage yang akan ditampilkannya.

- berikut hasilnya
![hasilnya](https://user-images.githubusercontent.com/56240533/116884859-6ca4cc00-ac51-11eb-83e3-922bdf35f106.png)

- SOURCE KODE "HISTOGRAM IMAGE"

function varargout = lailah(varargin)
% LAILAH MATLAB code for lailah.fig
%      LAILAH, by itself, creates a new LAILAH or raises the existing
%      singleton*.
%
%      H = LAILAH returns the handle to a new LAILAH or the handle to
%      the existing singleton*.
%
%      LAILAH('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in LAILAH.M with the given input arguments.
%
%      LAILAH('Property','Value',...) creates a new LAILAH or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before lailah_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to lailah_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help lailah

% Last Modified by GUIDE v2.5 02-May-2021 20:03:13

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @lailah_OpeningFcn, ...
                   'gui_OutputFcn',  @lailah_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before lailah is made visible.
function lailah_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to lailah (see VARARGIN)

% Choose default command line output for lailah
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes lailah wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = lailah_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;


% --- Executes on button press in open_image.
function open_image_Callback(hObject, eventdata, handles)
[namafile, formatfile] = uigetfile('*.png; *.bmp; *.jpg', 'membuka gambar'); %memilih gambar
if formatfile == 0
    return;
end
image = imread([formatfile, namafile]);
guidata(hObject, handles);
axes(handles.axes1); 
imshow(image); 

gambarhist = fullfile(formatfile, namafile);
set(handles.path_image,'String', gambarhist);

red = image(:,:,1);
green = image(:,:,2);
blue = image(:,:,3);
r = imhist(red);
g = imhist(green);
b = imhist(blue);
x = 0:255;
set(handles.uitable1,'data',r);
set(handles.uitable2,'data',g);
set(handles.uitable3,'data',b);

axes(handles.axes2)
plot(x,r,'r-')

axes(handles.axes3)
plot(x,g,'g-')

axes(handles.axes4)
plot(x,b,'b-')
[namafile, formatfile] = uigetfile('*.png; *.bmp; *.jpg', 'membuka gambar'); %memilih gambar
if formatfile == 0
    return;
end
image = imread([formatfile, namafile]);
guidata(hObject, handles);
axes(handles.axes1); 
imshow(image); 

gambarhist = fullfile(formatfile, namafile);
set(handles.path_image,'String', gambarhist);
red = image(:,:,1);
green = image(:,:,2);
blue = image(:,:,3);
r = imhist(red);
g = imhist(green);
b = imhist(blue);
x = 0:255;
set(handles.uitable1,'data',r);
set(handles.uitable2,'data',g);
set(handles.uitable3,'data',b);

axes(handles.axes2)
plot(x,r,'r-')

axes(handles.axes3)
plot(x,g,'g-')

axes(handles.axes4)
plot(x,b,'b-')
% hObject    handle to open_image (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)



function path_image_Callback(hObject, eventdata, handles)
% hObject    handle to path_image (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of path_image as text
%        str2double(get(hObject,'String')) returns contents of path_image as a double


% --- Executes during object creation, after setting all properties.
function path_image_CreateFcn(hObject, eventdata, handles)
% hObject    handle to path_image (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

