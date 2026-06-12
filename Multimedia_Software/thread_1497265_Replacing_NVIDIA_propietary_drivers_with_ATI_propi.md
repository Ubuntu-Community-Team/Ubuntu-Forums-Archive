---
title: "Replacing NVIDIA propietary drivers with ATI propietary drivers"
date: 2010-05-30
forum: Multimedia Software
---

### Post by yozgoesdigital on 2010-05-30
Just bought a Saphire ATI Radeon HD 5670 graphic card to replace my NVIDIA 7300 GS. For getting my Kubuntu working again I need to delete my NVIDIA drivers and get the proprietary ATI drivers since the open source drivers are not working with the 5XXX series. Right now I can not get it to work or into graphic environment (and I am not a bash genius).

Somebody has suggestions?

What I tried already:
- If I try to start Kubuntu I get an error message that no NVIDIA card can be found, but I can not get into any graphic environment.

- Installed Fglrx ```
sudo apt-get install fglrx
``` But then it still wants to load the NVIDIA drivers. (maybe xconfig is not updated??)

- Could get the live cd working with the code provided in another thread ([link]("http://ubuntuforums.org/showthread.php?t=1463961&page=3")).
```
live-install xforcevesa
``` Could such a command also be applied for an installed version?

---

