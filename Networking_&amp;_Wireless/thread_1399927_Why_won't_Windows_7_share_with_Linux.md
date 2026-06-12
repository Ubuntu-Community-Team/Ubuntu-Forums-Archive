---
title: "Why won't Windows 7 share with Linux?"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by the lemming on 2010-02-06
At first I thought it was me and and my limited knowledge of computers which was stopping me from sharing files between my Windows 7 and my Linux computers.  I'd tried everything that I could think of and asked as many questions as I could on here and the Mint forums but got nowhere.

I then tried an experiment where I fired up a Live CD in the computer that normally runs Windows 7 and booted up the other computer into Vista.

Guess what?

I was able to share files instantly between Vista and linux systems with no faffing or fussing what so ever.

I know that Linux and Samba are not the problem now but it all has to do with Windows 7 not playing nicely.

Anybody know how long it will be before Linux cracks this little problem?

---

### Post by johnson.d on 2010-02-09
I am able to share a folder in Windows 7, and also I can access the folder from Ubuntu. May be the problem in your case lies with the windows sign in assistant. You can probably try uninstalling the sign in assistant in windows 7 and try again.

Start menu -> Control Panel -> Programs
Select Windows Live ID Sign-in Assistant -> Click Uninstall

---

### Post by the lemming on 2010-02-12
Hello chaps

This morning I uninstalled Windows Live ID Assistant in the hope of getting my computers to share files.

While running a Live CD of Ubuntu 9-10 and Mint 8 I got the same error message saying that I was unable to mount location.  Failed to retrieve share list from server.

Any ideas what I can do next?

---

### Post by Fire_Chief on 2010-02-12
Firewall and/or public sharing settings in Win7 perhaps?

---

### Post by the lemming on 2010-02-12
I quickly tried with the Firewall turned off but no joy.

As for permissions, I have everything that I can think of to allow everything access to my Windows 7 computer, but still no joy.

Samba works with Vista and XP but not Windows 7

Aggg

---

### Post by WannabeFantasma on 2010-02-12
I had it running earlier...

Try a thread about samba sharing from "dmizer"
He has a thread that can help!

---

### Post by johnson.d on 2010-02-18
You can try the following command to check the folders shared in Windows 7 machine:

$ smbclient -L <ip-address>

We can check whether it is able retrieve the share list from the Windows 7 machine. You can also check whether Windows is accepting Samba connections, using the following command.

$ telnet <ip-address> 445

You can see Windows logs, as it would be useful to find the reason for connection failure to the share.
You can also install wireshark to capture the details of the connection and we can confirm whether the request is reaching the server.

---

### Post by jackportd on 2010-02-18
Hi,
The reason why Windows has a large percentage of the market share is not because it is technically superior to Linux. It is because a large percentage of computer users don't know squat about their computers. Couple that with the fact that Microsoft virtually owns most of the distribution channel.
So, the reason why Vista has 10 times market share than Linux is because...., well, I know you have a brain to understand why.
Now, do you think Windows will still have the largest share of the pie if the situation is reversed? I don't think so!
What about viruses? Almost 30 years and still Windows is plagued by viruses? My boss can't stand the presence of a defect in our products for just one day and here we have Microsoft sleeping on the biggest defect of their biggest product? It surely makes Windows a big joke!

---

### Post by Jamina1 on 2010-02-18
I'm having a similar problem between my laptop (running 9.10) and my desktop (running Win 7).

I have shared my "downloads" folder, but my linux laptop cannot read the share. The Public folders are shared just fine, but my laptop can't see preexisting files in the Users->Public->Games folder (specifically trying to copy WoW over onto my laptop). I created a folder from my linux laptop IN the public share and it appeared in the windows folder. I can create copies of files and they appear, but the original folder WILL NOT SHOW UP, even if I rename it.

I am confused and a bit angry.

---

### Post by the lemming on 2010-02-24
Just re-installed Mint 8 onto my laptop and it it is now sharing files with Windows 7 out of the box.  No fiddling required, which is nice.

I haven't tried this on Ubuntu yet but I assume that everything will be working perfectly fine there as well.

Cheers

---

### Post by coskierken on 2010-02-24
I have found Nautilus has a problem with shares sometimes.  Dolphin (file manager) has no problem with shares at all.  You can even do a split screen for a little easier view and simpler drag and drop.  Glad to hear it cleared up with Mint.  I don't know what file manager it uses.

---

### Post by ChuckV on 2010-06-15
I was having a similar problem, uninstalling Windows Live Sign-In Assistant fixed it for me.  I can now see my Windows shares and printer from my Linux system.

---

### Post by xenosaga456 on 2010-06-15
hey i fixed mine i just

```
sudo nautilus
```

then i browsed from there to my windows partition and i changed the permissions that fixed it for me and my windows still works fine

---

