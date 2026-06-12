---
title: "how to run zbrush in ubuntu 14.04"
date: 2014-07-07
forum: Multimedia Software
---

### Post by frankyboynl on 2014-07-07
hello, I am stuck here with a file called zbrush.exe, which doesn't run under the newest version of wine in ubuntu trusty. can anyone help me?



grtz, Frank

---

### Post by kc1di on 2014-07-07
you could install play on linux and try that. it lets you select the version of wine you want to use for each program you install on it.

you can install it in a terminal with this command ```
sudo apt-get install playonlinux
```
good luck

---

### Post by frankyboynl on 2014-07-07
when I do that, playonlinux crashes on startup. maybe it has something to do with the wine version...


thnx, Frank

---

### Post by kc1di on 2014-07-07
Try launching if from a terminal  and post any error message you get here.

---

### Post by frankyboynl on 2014-07-07
I ran wine ZBrush.exe, but it only pauses a while and then stops, no error messages..


grtz, Frank

---

### Post by kc1di on 2014-07-07
you have to install the ZBrush program in Playon Linux  just like you would if your running windows.

---

### Post by frankyboynl on 2014-07-07
I did that, but in the message box of playonlinux it gives an error message...




grtz, Frank

---

### Post by kc1di on 2014-07-07
What does the error message say?

---

### Post by frankyboynl on 2014-07-07
Error in POL_Wine
Wine seems to have crashed

If your program is running, just ignore this message

---

### Post by frankyboynl on 2014-07-08
I tried it with the newest version of wine, but then I get the following error message:

 wine ZBrush.exe
fixme:iphlpapi:NotifyAddrChange (Handle 0xd9e288, overlapped 0xd9e2a0): stub
fixme:dwmapi:DwmIsCompositionEnabled 0x6b238dcc
fixme:iphlpapi:NotifyAddrChange (Handle 0xdbe880, overlapped 0xdbe88c): stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:server_ioctl_sock Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
fixme:ntdll:server_ioctl_file Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:server_ioctl_sock Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
wine: configuration in '/home/frank/.wine' has been updated.
frank@frank-K70IJ:~/Downloads/Pixologic ZBrush 4R4 Portable Preactivated ---PMS$  wine ZBrush.exe
err:ntdll:RtlpWaitForCriticalSection section 0x7ebcd760 "user_main.c: user_section" wait timed out in thread 0009, blocked by 0023, retrying (60 sec)

---

### Post by kc1di on 2014-07-08
Was this program running in older versions of Wine? 
If so you may want to try an older version say 1.4 instead of 1.6.

---

### Post by frankyboynl on 2014-07-08
strange, when I tried to install the older version of Wine, it automatically installed 1.6 in synaptic...


grtz, Frank

---

### Post by kc1di on 2014-07-08
you may want to try completely removing wine 1.6 and try installing 1.4

---

### Post by frankyboynl on 2014-07-08
thats my point, when I install wine 1.4 it automaticcaly installs 1.6, and when I try to remove 1.6, it also deletes 1.4...


grtz, Frank

---

### Post by kc1di on 2014-07-08
Well if they are both installed you should be able to choose the one you want to use in play on linux. When you install zbrush.

---

### Post by frankyboynl on 2014-07-08
ah yes, I was able to do that, but unfortunately Zbrush wouldn't start under 1.4, same error message...



grtz, Frank

---

### Post by kc1di on 2014-07-09
As I don't run Zbrush I don't know what else to tell you to try. It's most likely a missing dependency. But would have no clue what to tell you look for at this point.  Maybe someone will come along who has more experience with that particular program. Good Luck. one other possibility would be to set up windows in a Virtual Machine on Ubuntu - Then it would run.  Virtual box is included free in the software repository.

---

### Post by frankyboynl on 2014-07-09
thanks anyway!



grtz, Frank

---

### Post by jarmade on 2014-07-09
Don't bother trying to get Zbrush to work in wine. I have tried many times, on many different distros and wine versions, you can get it to open and sculpt fine, but the main issues are the freezing on start up, for a solid 5 minutes or more and then the main problem is the wacom tablet pressure, it works on and off, the pressure sensitivity will randomly stop working and then you have to restart the program, then wait for 10 minutes for it to load back up, i have tested it many times on different enviroments and its always the same...

Zbrush is the only piece of software i need to finally throw windows in the trash, i wish they would make a native version, they already have a mac version, so the code must be already written in a cross platform way.

---

