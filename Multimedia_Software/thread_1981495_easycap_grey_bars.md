---
title: "easycap grey bars"
date: 2012-05-16
forum: Multimedia Software
---

### Post by binx24 on 2012-05-16
I have a easycap ID 05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device which shows up with grey bars after about 5 seconds in VLC. I can get it to work by typing:sudo rmmod easycap
sudo modprobe easycap 'bars=0'
into the terminal. I was hoping that there was a way to have this command run automatically when I insert the easycap device as I am not the only one who will use it. I am using ubuntu 12.04. I am very new to Ubuntu and don`t know much about writing commands/scripts. I am sorry if I have posted this in the wrong spot. Any help would be greatly appreciated.

---

### Post by enigma32 on 2012-05-17
You can permanently apply that kernel module option by adding it to the modprobe config.

Try something like:

```
cd /etc/modprobe.d
sudo gedit easycap.conf
```
(it'll ask you for your password)

and put this into the text editor:
```
# Fix grey bars problem
options easycap bars=0
```
Then save and reboot.


If if DOESN'T HELP, you should clean up that attempt:
```
sudo rm -f /etc/modprobe.d/easycap.conf
```


Hope this helps,
Matt

---

### Post by binx24 on 2012-05-17
Thankyou for the reply. I can finally plug in the easycap and it works without putting any commands in terminal. I have been pulling my hair out trying to work this out and was getting nowhere. Thankyou.

---

### Post by enigma32 on 2012-05-17
My pleasure. Glad it worked out. Don't forget to mark your thread as solved!
-Matt

---

