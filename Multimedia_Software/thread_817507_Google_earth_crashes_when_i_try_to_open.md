---
title: "Google earth crashes when i try to open?"
date: 2008-06-03
forum: Multimedia Software
---

### Post by Kidfork on 2008-06-03
Hello, i just installed google earth about yesterday. I tryed installing it through terminal, synaptic, and even the google earth downlaod site. The problem is. When i try to open it through the app. menu it just doesn't open. WHen i try to open it through terminal i get this:

tyler@tyler-desktop:~$ googleearth
Google Earth has caught signal 4.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin [0x804f3c7]
  /usr/lib/googleearth/googleearth-bin [0x804f8ed]
  [0xb7f17420]
  /usr/lib/googleearth/libbase.so(_ZN5earth17ScopedPerfSetting6createERK7QStringbb+0x64) [0xb70600f2]
  /usr/lib/googleearth/libbase.so(_ZN5earth17ScopedPerfSettingC2ERK7QStringbb+0x45) [0xb706018b]
  /usr/lib/googleearth/libbase.so(_ZN5earth20LogScopedPerfSettingC1ERK7QString+0x35) [0xb7060257]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application13setupQtLocaleEv+0x42) [0xb7285a60]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x31) [0xb7285da9]
  /usr/lib/googleearth/googleearth-bin(main+0x2a1) [0x8050b77]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70af450]
  /usr/lib/googleearth/googleearth-bin [0x804f201]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/tyler/.googleearth/crashlogs/crashlog-0B7A2AE4.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.


It does the same thing everytime. O and here are my specs.

2.4 GHZ INTELL PROCESSER
640MB RAM
UBUNTU 8.04 HARDY
30GB OF HDD SPACE.



IT INSTALLS FINE BUT WHEN I TRY TO OPEN IT JSUT DOESN'T.

---

### Post by Kidfork on 2008-06-03
Bump

---

### Post by Kidfork on 2008-06-05
Bump

---

### Post by lisati on 2008-06-05
Don't panic, your question has been spotted.

I initially had trouble with Google Earth crashing when I had it on Feisty (7.04) on my laptop and found that I had to enable 3d graphics acceleration on the "restricted drivers"

Hope this helps.

---

### Post by Kidfork on 2008-06-05
WHen is "recticted drivers"?

---

### Post by xc3RnbFO8P on 2008-06-05
> 2.4 GHZ INTELL PROCESSER
640MB RAM
UBUNTU 8.04 HARDY
30GB OF HDD SPACE.

and your graphic card?

---

### Post by gandaran on 2008-06-05
to run google earth you need a 3d video/graphics card, do you have it?
run this command on a terminal «**lspci**» and post the results here.

---

### Post by Kidfork on 2008-06-05
tyler@tyler-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:07.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by Kidfork on 2008-06-05
.

---

### Post by xc3RnbFO8P on 2008-06-05
In System> Administration> Hardware Driver
did you enable **Nvidia accelerated graphics driver**?

---

### Post by Kidfork on 2008-06-07
Yes i know this because i can play high-graphic card games and my built-in graphics is only 16mb and i also checked, its checked.

---

### Post by xc3RnbFO8P on 2008-06-08
Uninstall Google-Earth in Synaptic Package Manager (Complete Removal)
Install GoogleEarthLinux.bin 
In Terminal:
> sudo -i /home/your folder/desktop/GoogleEarthLinux.bin <return>
or type **sudo -i** and drag/drop GoogleEarthLinux.bin into Terminal window <return>

[http://ubuntuforums.org/showpost.php?p=4916245&postcount=1]("http://ubuntuforums.org/showpost.php?p=4916245&postcount=1")

---

### Post by Kidfork on 2008-06-15
YEs it is.

---

