---
title: "problems installing audacity 1.3.3beta"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by pollywog on 2007-08-20
Hello- I'm trying to install the new version of audacity -1.3.3 beta- from source code on a Feisty system. The "Make"  step is unsuccessful, returning more errors than I can count.  I'm trying to install this alongside an older version of Audacity, but I've tried uninstalling the older version, and the "Make" step yields the same results. I was following the ubustu instructions for setting up 1.3.2:
```
sudo apt-get install build-essential libwxgtk2.6-0 libmad0 libsndfile1 libwxgtk2.6-dev gettext
``` 

```
./configure --program-suffix=beta && make
```

And here is the last part of my terminal dialog:

generic/../gtk/FileDialogPrivate.h:34: error:                 FileDialog::FileDialog(wxWindow*, const wxString&, const wxString&, const wxString&, const wxString&, long int, const wxPoint&)
generic/../gtk/FileDialogPrivate.h:26: error:                 FileDialog::FileDialog()
generic/FileDialogPrivate.cpp: In constructor ‘FileDialog::FileDialog(wxWindow*, const wxString&, const wxString&, const wxString&, const wxString&, long int, const wxPoint&, bool)’:
generic/FileDialogPrivate.cpp:950: error: type ‘wxFileDialogBase’ is not a direct base of ‘FileDialog’
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:963: error: no ‘bool FileDialog::Create(wxWindow*, const wxString&, const wxString&, const wxString&, const wxString&, long int, const wxPoint&, bool)’ member function declared in class ‘FileDialog’
/usr/include/wx-2.6/wx/generic/filedlgg.h: In member function ‘bool FileDialog::Create(wxWindow*, const wxString&, const wxString&, const wxString&, const wxString&, long int, const wxPoint&, bool)’:
/usr/include/wx-2.6/wx/generic/filedlgg.h:104: error: ‘bool wxGenericFileDialog::m_bypassGenericImpl’ is private
generic/FileDialogPrivate.cpp:966: error: within this context
/usr/include/wx-2.6/wx/generic/filedlgg.h:104: error: ‘bool wxGenericFileDialog::m_bypassGenericImpl’ is private
generic/FileDialogPrivate.cpp:974: error: within this context
generic/FileDialogPrivate.cpp:1090: error: expected type-specifier before ‘FileCtrl’
generic/FileDialogPrivate.cpp:1090: error: cannot convert ‘int*’ to ‘wxFileCtrl*’ in assignment
generic/FileDialogPrivate.cpp:1090: error: expected `;' before ‘FileCtrl’
generic/FileDialogPrivate.cpp:1124: error: ‘m_choicesizer’ was not declared in this scope
/usr/include/wx-2.6/wx/generic/filedlgg.h: In destructor ‘virtual FileDialog::~FileDialog()’:
/usr/include/wx-2.6/wx/generic/filedlgg.h:104: error: ‘bool wxGenericFileDialog::m_bypassGenericImpl’ is private
generic/FileDialogPrivate.cpp:1158: error: within this context
generic/FileDialogPrivate.cpp: In member function ‘virtual int FileDialog::ShowModal()’:
generic/FileDialogPrivate.cpp:1181: error: ‘m_choicesizer’ was not declared in this scope
generic/FileDialogPrivate.cpp: At global scope:
generic/FileDialogPrivate.cpp:1210: error: no ‘void FileDialog::DoSetFilterIndex(int)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1259: error: no ‘void FileDialog::OnChoiceFilter(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1264: error: no ‘void FileDialog::OnCheck(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1269: error: no ‘void FileDialog::OnActivated(wxListEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1274: error: no ‘void FileDialog::OnTextEnter(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1281: error: no ‘void FileDialog::OnTextChange(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1300: error: no ‘void FileDialog::OnSelected(wxListEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1329: error: no ‘void FileDialog::HandleAction(const wxString&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1458: error: no ‘void FileDialog::OnListOk(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1463: error: no ‘void FileDialog::OnList(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1472: error: no ‘void FileDialog::OnReport(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1481: error: no ‘void FileDialog::OnUp(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1490: error: no ‘void FileDialog::OnHome(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1499: error: no ‘void FileDialog::OnNew(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1508: error: no ‘void FileDialog::OnExtra(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1591: error: no ‘void FileDialog::UpdateControls()’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:86: warning: ‘int FileDataNameCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:98: warning: ‘int FileDataSizeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:112: warning: ‘int FileDataTypeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:126: warning: ‘int FileDataTimeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:409: warning: ‘sm_eventTableEntries’ defined but not used
make[2]: *** [generic/FileDialogPrivate.o] Error 1
make[2]: Leaving directory `/home/matt/audacity-src-1.3.3/lib-src/FileDialog'
make[1]: *** [FileDialog-recursive] Error 2
make[1]: Leaving directory `/home/matt/audacity-src-1.3.3/lib-src'
make: *** [audacity] Error 2
matt@matt-desktop:~/audacity-src-1.3.3$ 


Does anyone have any idea what I'm doing wrong? Thanks P.W.

---

