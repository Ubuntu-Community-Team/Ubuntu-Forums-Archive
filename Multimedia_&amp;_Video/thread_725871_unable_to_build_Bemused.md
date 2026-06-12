---
title: "unable to build Bemused"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by sDoky on 2008-03-16
Hi, I'm tryimg to get working this application - [http://bemused.sourceforge.net/](http://bemused.sourceforge.net/) . It says just ```
sudo make install
```but it makes tons of errors...

```
sdoky@sdoky-desktop:~/bemusedlinuxserver1.73$ make
g++ -o bemusedlinuxserver -I/usr/include/xmms -I./ -lxmms -lbluetooth `gtk-config --libs --cflags` main.cpp BemusedServerDlg.cpp
./BemusedServerDlg.h:66: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’
./BemusedServerDlg.h:67: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’
./BemusedServerDlg.h:68: error: extra qualification ‘CBemusedServerDlg::’ on member ‘WriteFile’
./BemusedServerDlg.h:69: error: extra qualification ‘CBemusedServerDlg::’ on member ‘WriteFile’
./BemusedServerDlg.h:70: error: extra qualification ‘CBemusedServerDlg::’ on member ‘GetLastError’
./BemusedServerDlg.h:102: error: extra qualification ‘CBemusedServerDlg::’ on member ‘AddBookmarks’
BemusedServerDlg.h:66: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’
BemusedServerDlg.h:67: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’
BemusedServerDlg.h:68: error: extra qualification ‘CBemusedServerDlg::’ on member ‘WriteFile’
BemusedServerDlg.h:69: error: extra qualification ‘CBemusedServerDlg::’ on member ‘WriteFile’
BemusedServerDlg.h:70: error: extra qualification ‘CBemusedServerDlg::’ on member ‘GetLastError’
BemusedServerDlg.h:102: error: extra qualification ‘CBemusedServerDlg::’ on member ‘AddBookmarks’
make: *** [bemusedlinuxserver] Error 1
sdoky@sdoky-desktop:~/bemusedlinuxserver1.73$ 
```
and then I'm unable to install... Please tell me what I'm doing wrong... I'm not sure about the dependencies either cause there's no info for that matter. Thanks for help

---

### Post by jjrp78 on 2008-04-22
may be too late but check out this thread:

[http://ubuntuforums.org/showthread.php?t=132352](http://ubuntuforums.org/showthread.php?t=132352)

..about some of the errors you are getting I read somewhere that some stuff changed in the C compiler so to solve this:

./BemusedServerDlg.h:66: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’

open the file BemusedServerDlg.h go to line 66 and erase ‘CBemusedServerDlg::’ (without the quotes).

---

### Post by sDoky on 2008-04-27
Thanks a lot, I'll try that.

> **jjrp78 said:**
> may be too late but check out this thread:

[http://ubuntuforums.org/showthread.php?t=132352](http://ubuntuforums.org/showthread.php?t=132352)

..about some of the errors you are getting I read somewhere that some stuff changed in the C compiler so to solve this:

./BemusedServerDlg.h:66: error: extra qualification ‘CBemusedServerDlg::’ on member ‘ReadFile’

open the file BemusedServerDlg.h go to line 66 and erase ‘CBemusedServerDlg::’ (without the quotes).

---

