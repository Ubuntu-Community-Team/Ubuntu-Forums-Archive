---
title: "Microdia webcam problem"
date: 2011-02-09
forum: Multimedia Software
---

### Post by ciprianv on 2011-02-09
Hi

I bought a USB Microdia with microphone webcam (0c45:613b Microdia Win2 PC Camera) and i couldn't make it work on my Kubuntu 10.10 system.

I tried all sorts of instructions found on the web but without result. I also downloaded some drivers provided by[ these guys]("http://groups.google.com/group/microdia"), but those .deb packages are designed for k/ubuntu 7.04 systems, not 10.10. 

Do you have any ideea on how could i install & use my webcam?

---

### Post by realzippy on 2011-02-09
Since it seems to be a gspca camera,try reloading the gspca module.
[I also had this problem]("http://ubuntuforums.org/showthread.php?t=1439611") with a different,but also gspca-module driven camera in newer kernels.

edit:
And welcome to the forum!!

---

### Post by ciprianv on 2011-02-09
Ok, i haven't tried this out, but there's a small detail regarding my system: i also have a tv-tunner installed which is seen as /dev/video0. What should i do in this case?

---

### Post by realzippy on 2011-02-09
Nothing.Your cam -if it has not already,so your problem is similar-should
become video1 then...
....run gstreamer-properties to check this eg ....

Edit:
Btw,according to
[http://www.spinics.net/lists/linux-media/msg26226.html](http://www.spinics.net/lists/linux-media/msg26226.html)

your command to try might be
```
sudo modprobe -r gspca_sonixj
```
instead of gspca_sunplus aso.

---

### Post by ciprianv on 2011-02-09
Thanks for the welcoming and for the fast response RealZippy, but unloading and reloading the gspca module had no effect. The webcam programs (like Cheese) only detect my tv-tunner. There's no /dev/video1 or webcam.

Any other ideas that might work?

LE: dmesg returns these messages, if it might give you any clues:

[ 5158.044022] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 5158.216947] usb 2-1: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[ 5158.335008] usb 2-1: No supported image sensor detected for this bridge
[ 5161.807074] gspca: main v2.9.0 registered
[ 5161.808800] usbcore: registered new interface driver sonixj
[ 5161.808804] sonixj: registered

---

### Post by realzippy on 2011-02-09
Sorry,edited post #4...

---

### Post by ciprianv on 2011-02-09
I know. This is what i used:
sudo modprobe -r gspca_sonix

---

### Post by realzippy on 2011-02-09
No idea.Sorry,I only came along this thread because of the mentioned *gspca reloading bug* I was affected,I am not a ubuntu webcam expert;but others here are,so have a little patience.

[I]No supported image sensor detected for this bridge
[/I]
...sounds interesting.Happy googling!

---

### Post by no2498 on 2011-02-09
if you are using 32 bit not 64 bit
try wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

i think you can still get it in a deb file

you can change video 0 to 1
in this program

hope it helps you

---

