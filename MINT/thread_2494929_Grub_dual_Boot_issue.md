---
title: "Grub dual Boot issue"
date: 2024-01-31
forum: MINT
---

### Post by danffosddu on 2024-01-31
Upgraded mint. restarted into windows to do some work. When restarted again no grub option, only lenovo splash screen and 'image not loaded. Corrupt' error flashes up

Running live mint usb and install bott-repair. Summary gave below url:

[http://*******.us/m5SbKm](http://*******.us/m5SbKm)

Will boot-repair work

---

### Post by QIII on 2024-01-31
Moved to MINT.

---

### Post by Rubi1200 on 2024-02-01
URL seems not to work.

Please run the boot info summary again and paste the URL to the pastebin here.

---

### Post by danffosddu on 2024-02-01
URL: [http://*******.us/9MkXkP](http://*******.us/9MkXkP)

---

### Post by danffosddu on 2024-02-01
try to post URL as text; [http://*******.us/9MkXkP](http://*******.us/9MkXkP)

---

### Post by danffosddu on 2024-02-01
URL split over lines due to me not knowing how to stop this entry being reformatted

[http:///](http:///)
*******.us/
9MkXkP

---

### Post by danffosddu on 2024-02-01
[http://*******.us/9MkXkP](http://*******.us/9MkXkP)

---

### Post by danffosddu on 2024-02-01
URL split over lines due to me not knowing how to stop this entry being reformatted

http://
*******.us/
9MkXkP

---

### Post by danffosddu on 2024-02-01
Right I have no idea how to post the url without it being reformatted

 the missing word that has been asteerisked out is

URL split over lines due to me not knowing how to stop this entry being reformatted

*******

---

### Post by danffosddu on 2024-02-01
[URL="http://*******.us/ 9MkXkP"]
[http://*******.us/](http://*******.us/) 9MkXkP


[/URL]

---

### Post by danffosddu on 2024-02-01
Can someoone plese tell me how to post a url without it getting reformatted all the time !!!

---

### Post by QIII on 2024-02-01
Your URL is being reformatted because the word is given a vulgar definition in the Urban Dictionary in English.  It is a perfectly acceptable word in Germanic and Norse languages.

I would recommend using [https://paste.ubuntu.com](https://paste.ubuntu.com)

---

### Post by yancek on 2024-02-01
Did you follow the instructions at the boot repair site to upload the report to pastebin?  When boot repair finishes, you should see the URL needed to access it which you can then copy to your thread here.  That is the standard way so if it does not work, I don't know why.

Didn't see post 12 above which is likely the problem.

---

### Post by jeremy31 on 2024-02-02
I uploaded the report to [https://paste.ubuntu.com/p/PmcNZNQ4RD/](https://paste.ubuntu.com/p/PmcNZNQ4RD/) from the other site

---

### Post by oldfred on 2024-02-02
Do you get a grub menu?
Or is error before that, and then probably an UEFI setting.
Update may have updated UEFI firmware or ifyou manually updated firmware that reverts many settings to defaults.
Lenovo seems to have additional security settings beyond UEFI Secure Boot.
Review UEFI settings. May have setting like links below.

Lenovo T450 Problem with boot repair GRUB - Boot Lock issue
[https://ubuntuforums.org/showthread.php?t=2494747](https://ubuntuforums.org/showthread.php?t=2494747)
Lenovo Locked UEFI/BIOS setting:
[URL="https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg"]https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg

[/URL]The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

---

