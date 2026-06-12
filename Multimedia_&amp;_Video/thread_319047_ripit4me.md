---
title: "ripit4me"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by Zrock on 2006-12-15
well iv been working on this one for a week now... i have ripit4me installed with all associated programs... I have been unable to get ripit4me to run at all... dvd decriptor i can get to run but will not show my DVD rom drive no mater what i do, DVD shrink will run and is able to access the DVD  drive.. I have followed all teh forms and guides i could find with no luck... this is really starting to get frustrating... I have installed and unisalled severall times , reverted back to wine 9.5 or whatever it was. iv red teh help in this form so much i have it memorized...

---

### Post by cw1925 on 2006-12-15
[LEFT]It's most likely a Windows-only proggy.
[/LEFT]

---

### Post by Ethos on 2006-12-15
when you are starting dvd decrypter do you have wine set to windows nt? also have a disc in your drive before you start dvd decrypter, ALWAYS...

---

### Post by Trespasser on 2006-12-15
Zrock,
Go to this thread and read thru it:

[http://www.ubuntuforums.org/showthread.php?t=310836&highlight=ripit4me](http://www.ubuntuforums.org/showthread.php?t=310836&highlight=ripit4me)

It should help you get going. If you're running Feisty then you're on your own. Good luck.

---

### Post by Zrock on 2006-12-15
> **Ethos said:**
> when you are starting dvd decrypter do you have wine set to windows nt? also have a disc in your drive before you start dvd decrypter, ALWAYS...

yep it is set to windows nt and their was a cd in the drive... hopping that if i can get decripter to see the drive ripit4me will work

---

### Post by Zrock on 2006-12-15
> **Trespasser said:**
> Zrock,
Go to this thread and read thru it:

[http://www.ubuntuforums.org/showthread.php?t=310836&highlight=ripit4me](http://www.ubuntuforums.org/showthread.php?t=310836&highlight=ripit4me)

It should help you get going. If you're running Feisty then you're on your own. Good luck.

yep followed all those guides with no luck

---

### Post by Rumpanzle on 2006-12-15
Make sure you have the mfc42.dll in the right installation folder, there will be a Wine folder under root/.wine and under your user/.wine. If you use root then you have to copy the .dll there (system32), too. DVD Decrypter should work, if you set the drive type in winecfg to cd-rom, and make sure you do this winecfg as user and as root. Stick to wine 9.5 untill all runs.

---

### Post by tseliot on 2006-12-15
It works just fine on Dapper. It doesn't seem to work properly on Edgy though...

---

### Post by Rumpanzle on 2006-12-15
Edgy here, it runs like on windows. Took some time, see [HERE.]("http://www.ubuntuforums.org/showthread.php?t=310836")

---

### Post by Trespasser on 2006-12-15
(a) With the newer versions of Wine DVD Decrypter detects my drive D without a DVD in the tray.

(b) No need to run Wine under root. If you do root creates a new .wine in root folder (a waste of about 3 Mb).

(c) RipIt4Me runs just fine under Edgy but you got to install an older version of Wine first (0.9.5...works for both Dapper and Edgy or 0.9.15...which worked for me).

(d) After installing Wine run winecfg in Terminal then set OS from default Win 2000 to NT40. Then go to Drives tab > Click Auto Detect > highlight your DVD drive >click Show Advanced > then under Type select CD-ROM > click Apply (at bottom) and then OK.

(e) Also, here's a little trick I learned...in /home/user create a folder and name it .kde (folder will become hidden after you exit /home/user). By doing this when you install DVD Shrink and DVD Decrypter Wine will create Desktop icons for the two of them (I don't know if it's still necessary with the newer versions or not...I just automatically do it anymore). 

(f) Make sure you install mfc42.dll (the one linked in my thread) in /home/user/.wine/drive_c/windows/system32 before you install DVD Shrink or DVD Decrypter.

(g) You can create a RipIt4Me Desktop icon yourself by right-clicking in an open space on Desktop > select Create Launcher > fill in the name > select an icon > then paste this line into the Command section: wine "c:/Program Files/RipIt4Me/RipIt4Me.exe"

Have a good day. :) .

---

### Post by Zrock on 2006-12-16
well i seem to be getting someware now... now i can get the program to open but as soon as i click it to start it shuts down.... also everything seems to be squished in the program all the text is written on top of each other or their is no text in teh ripit4me prefrences or setup?

---

### Post by Zrock on 2006-12-16
just noticed something in the terminal window when i was trying to run ripit4me
libGL warning: 3D driver claims to not support visual 0x42
fixme:winecfg:mode_to_label translate me

---

### Post by Trespasser on 2006-12-16
Zrock,
You must be doing something wrong to get those type of results. What version of Ubuntu are you using?

Just start over from scratch.

Go into Synaptic and delete Wine. Next, go in to /home/user and delete .wine from there. Reboot your system. Now install Wine 0.9.5. Then go into Synaptic and Lock Version for Wine 0.9.5. Next, open Terminal and type winecfg as user (not root). Set OS to NT40. Go to Drives tab...click Auto Detect...highlight DVD drive...click Show Advanced...and under Type select CD-ROM...click Apply...then OK. Copy mfc42.dll to /home/user/.wine/drive_c/windows/system32. Install DVD Shrink, DVD Decrypter and RipIt4Me via Installer. 

My advice is if RipIt4Me is now working don't upgrade to the latest version of Wine (0.9.27). There's really no advantage to doing so. 0.9.5 works great.

---

### Post by Zrock on 2006-12-16
im running 6.10... i have went through teh above steps severall times.... seems like each time i get a new result..

---

### Post by Trespasser on 2006-12-16
You deleted Wine from Synaptic and .wine from /home/user, right? Also, you are using 0.9.5?

---

### Post by Zrock on 2006-12-16
yeppers

---

### Post by Trespasser on 2006-12-16
Zrock,
Do me a favor and uninstall everything again and as go thru the reinstall write down each step, no matter how small, and post it here. Also, how many CD/DVD drives do you have installed in your system?

---

### Post by Zrock on 2006-12-16
i just have one dvd drive in the system.... One thing i noticed in wine is that it is showing 2 drives... in wine

---

### Post by Trespasser on 2006-12-17
Mine shows two drives as well. Has been that way for the last 6 or 7 releases. Wine bug. If you notice Wine 0.9.5 doesn't list two drives.

---

### Post by Zrock on 2006-12-28
well after another week of searching and folowing the above directions i finally gave up and took Ubuntu of the computer... Everything i tryed came up with the same result... Still have ubuntu on my laptop to play with so maby in the future ill try it again on the other computer... Thanks for trying

---

### Post by PapaWiskas on 2007-02-18
> **Zrock said:**
> just noticed something in the terminal window when i was trying to run ripit4me
libGL warning: 3D driver claims to not support visual 0x42
fixme:winecfg:mode_to_label translate me

I get this same error message, and I have gone through all these install directions I don't know how many times.  RipIt4Me just crashes after clicking the wizard button.

---

