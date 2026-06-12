---
title: "ParticleIllusion SE with Wine. Any Solutions?"
date: 2009-07-31
forum: Multimedia Software
---

### Post by ArmenianLeader4 on 2009-07-31
I am currently using wine to run particleillusion SE by wondertouch, and it seems to open fine, but as the window appears, a small error box appears that reads: "DLL Loading error: WMVcore.DLL" and then the program closes. I am aware that this is probably due to the lack of a WMV Codec on Ubuntu 9.04, but does anyone know where or how I can get a solution to this problem? It would be appreciated.

Oh, and also, I am installing Sony Vegas 9 Platinum and Pinnacle 12 Ultimate with wine very soon, just as soon as I get the discs back. I don't know if they can provide a codec or if they help at all, but I thought I'd let you know.

---

### Post by vinutux on 2009-07-31
All the programs you mentions earlier is windows apps......it use an emulater called "wine" and running top of wine......so don't expected that programs runs smooth as they run in windows

---

### Post by ArmenianLeader4 on 2009-08-02
I understand that they may not run as smoothly, but all I need is the codec... so I think... I'm just asking if anyone knows where to find it or where to repair the .dll

---

### Post by overfloat on 2009-10-20
if you are still trying to get this to work...try this

get the DLL from here: [http://www.dlldump.com/download-dll-files_new.php/dllfiles/W/wmvcore.dll/9.00.00.3250/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/W/wmvcore.dll/9.00.00.3250/download.html)

and put it in:
your-home-directory/.wine/drive_c/windows/system32

---

