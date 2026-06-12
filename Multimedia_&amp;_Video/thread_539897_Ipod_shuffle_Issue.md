---
title: "Ipod shuffle Issue"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by will_i_am on 2007-08-31
My daughter has a 1gig I-pod shuffle. On my XP box the thing has no songs and is empty. When you mount it in Ubuntu it shows zero free memory. Yet only 315 k of used space. What am I missing here?  We are using both Amarock and Rhythm box to manage it. Any help will be appreciated. 



Will_i_am

---

### Post by Dark Hornet on 2007-09-01
Can you please provide some more details---for example: Is there supposed to be anything on the iPod?  When your XP box sees it, what program are you using, or are you just viewing it as a hard drive, and when you connect to Amarok, etc...will it allow you to add songs?

---

### Post by TryMe on 2007-09-01
This is usually because on the hidden .trash folder.
[https://answers.launchpad.net/ubuntu/+question/1904]("https://answers.launchpad.net/ubuntu/+question/1904")

To fix:
Open the drive under Nautilus and hit ctrl + H to show hidden files. If you see a folder named .trash delete it.

---

### Post by tgalati4 on 2007-09-01
To save wear and tear to flash memory, a writing scheme is used to completely fill the memory before it gets wiped and filled again.  On a mac, this is transparent.  On Linux, you have to manually empty the trash to regain the space.

---

### Post by TryMe on 2007-09-01
tgalati4 I don't understand exactly what you mean by "On a mac, this is transparent." but the reason for the .trash folder the to protect against accidental deletion. It is stored on the usb device for two reasions 
a) it would take up loads of unnecessary space on the main drive
b) speed of use. (can you imagine transferring all that data to the main drive every time. SLOW)
I believe the issue is going to be fixed in the 7.10 ubuntu by making ubuntu more aware of music players.

Anyway to prevent the issue hold down the shift key when deleting. This will skip the trash bin. Amarok does do this automatically I think.

---

### Post by will_i_am on 2007-09-01
The trash folder is not there when I show hidden. Amarok does not allow me to add songs. In XP I have looked at it through both the windows explorer and i Tunes (which allows the writing of songs). Hope this helps.

Will_i_am

---

### Post by TryMe on 2007-09-01
can you post the output of dmesg command please.

might be a permissions issue with the ipod connected to pc  try:
 chmod +w "/media/IPOD"
IPOD should be the name of your ipod all caps

---

