---
title: "Wireless Network Password 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by TheVisitors on 2010-04-30
So it would seem a bug which never got addressed in 9.10 (even 9.04 if I remember) has crossed over into The Final Build of 10.04. 

Wireless keeps asking for the network password. :(

The card works with the correct driver Ubuntu automatically selected (even tried the Windows Driver) & it sees my network (as well as the neighbors), but continues to always ask for the network key (using WPA2 Personal).

Can connect using Windows 7 & SuSe 11.2 (even 11.3 milestone 6), but not Ubuntu on either The Live CD or upon Desktop Install.


**** SOLVED ****
[http://ubuntuforums.org/showpost.php?p=9209394&postcount=8](http://ubuntuforums.org/showpost.php?p=9209394&postcount=8)
**** SOLVED ****

---

### Post by TheVisitors on 2010-04-30
Still no luck with this. I posted this on another forum & it seems I am not the only person with this problem.

---

### Post by heve on 2010-04-30
Hi, i'm having the same problem. With karmic my old notebook used to work fine -my netbook is still karmic and works ok. but, now with Lucid can't get connection. It (encore wireless card) sees the router, but gives the message "incorrect password".

---

### Post by TheVisitors on 2010-04-30
I'm thinking its not the card we're using....

I'm using a ASUS PCE-N13 & have a WRT160N Router.

I can connect if I turn off security (but that not smart)

---

### Post by deg12 on 2010-04-30
Same problem here. Wireless visible yet asks over and over again for password. At first it worked for a while and then it stopped. Doesn't seem to work without password protection either. Had no problems in 9.10

---

### Post by germanix on 2010-04-30
I too stumbled on a problem with my password for WAP/WAP2. The problem I got was that I was unable to enter my password. My password contains the @ sign in it and Ubuntu 10.4 would not let me type this @ sign into the password. I was forced to go into my router and change my password so it no longer had the @ sign in it and was then able to enter the new password. After that I had the re-configure the settings in System preferences/Network after which it did connect.
I am not sure if this is a bug in my case, find it strange however that I was not able to enter the password as is has been for years. I had no problem entering this same password in previous Ubuntu or Linux Mint versions.

---

### Post by chlorinekid on 2010-04-30
im having the same issue with 10.04. ive installed 10.04 netbook remix on my netbook and that finds and wireless and connects no problem. however the desktop won't connect for some reason. it finds the wireless and asks for the passkey but after trying to connect for a minute or so just aks for the password again.. i noticed this with the alpha and beta releases but sort of hoped it would be sorted by the time the final version was released. looks like i might have to drop back to 9.10.

if this bug documented anywhere? is it recognized?

---

### Post by TheVisitors on 2010-05-01
:KS **** SOLVED **** :KS

So I was able to connect when my router was unsecured, but never when it was secure.

I tested the following fixes on several computers & network setups on my PC & a few friends (10 network setups in total). Assuming you can not directly connect, you will need to either log into another OS which can connect through you wireless or re-set your router to turn OFF wireless security before you continue. 

80% Fix 1: Install either RutilT WLAN MANAGER  --- or ---- wICD
The default manager will ALWAYS ask for the password.

15% Fix 2: If you are using WPA2 Personal, switch to WPA1 Personal. 
It seems for some reason a few setups would not work on WPA2 (don't know why).

4% Fix 3: If your router has the option to use only N standard & you have selected this option, switch to either  MIXED (or Standard G).

1 % Fix 4: Do all the above. (worse case)

I tested this on several networks (different computers, network cards, routers, even 1 Apple) & this was my best way of fixing the problem on my pc & the friends who I knew that wanted to use Ubuntu 10.04, but was having the same problem.

---

### Post by NissanSkylineN1 on 2010-05-01
Hey,
Do you know how I can get these two programs on fix 1 on Windows and then transfer to Ubuntu? It would be helpful if all the links to the depended packages are also provided.
Thanks

---

### Post by TheVisitors on 2010-05-01
> **NissanSkylineN1 said:**
> Hey,
Do you know how I can get these two programs on fix 1 on Windows and then transfer to Ubuntu? It would be helpful if all the links to the depended packages are also provided.
Thanks

If you're new, its always best to install it through the package manager within Ubuntu (Ubuntu Software Center).... Its why I recommend people either direct connect or turn off security temporarily to apply these fixes.

But if you want the full package...

[http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)  --- download 

[http://wicd.sourceforge.net](http://wicd.sourceforge.net) ---detail info (I'd read it)


edit:  After you've got it installed (correctly).... Reboot (found it works best to do it).

---

### Post by NissanSkylineN1 on 2010-05-01
> **TheVisitors said:**
> If you're new, its always best to install it through the package manager (within Ubuntu).... Its why I recommend people either direct connect or turn off security temporarily to apply these fixes).

But if you want the full package...

[http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)  --- download 

[http://wicd.sourceforge.net](http://wicd.sourceforge.net) ---detail info (I'd read it)

The problem is that if I turn security off, every computer which will be on during that period of time will need their internet settings adjusted. That's about 5 computers. So, I need to download on windows and boot into Ubuntu. BTW, are all depedencies met with the package?

---

### Post by TheVisitors on 2010-05-01
No, I do not believe so. Had a hard time finding them independently.

However the following package "should"

[http://packages.ubuntu.com/lucid/net/wicd](http://packages.ubuntu.com/lucid/net/wicd)

Directly from Ubuntu. But I'd still do some reading if you plan on doing it that way.

---

### Post by NissanSkylineN1 on 2010-05-01
I installed it and rebooted and the program works. But, it still can't connect. It gets stuck at validating connection.

---

### Post by TheVisitors on 2010-05-01
> **NissanSkylineN1 said:**
> I installed it and rebooted and the program works. But, it still can't connect. It gets stuck at validating connection.

Hoping one of my friends wasn't having a firmware or driver problem, I removed her network from the list & then re-applied it (scanned for it).

If something as simple as that doesn't work then you may need to change from WPA2 to WPA1. Also if your router has the option to run in N only, change it to MIXED.... Mixed will still broadcast N Standard, but will also broadcast G Standard.

Beyond that it could be a driver problem (which is not easy task to resolve sometimes).

---

### Post by NissanSkylineN1 on 2010-05-01
Nope, didn't work.

---

### Post by NissanSkylineN1 on 2010-05-01
Ok, this is ridiculous. How can the Ubuntu developers expect us to not use WPA2? Are there any other distros of Linux hat support Wpa2? I'm seriously considering switching.

---

### Post by TheVisitors on 2010-05-01
> **NissanSkylineN1 said:**
> Ok, this is ridiculous. How can the Ubuntu developers expect us to not use WPA2? Are there any other distros of Linux hat support Wpa2? I'm seriously considering switching.

Ubuntu is "made" to support WPA2, but I think they have a few "Bugs" or driver conflicts which is preventing some people from using The Default Wireless Manager, WPA2, or full N Standard.

Give them some time & I'm sure they will in time fix it (I hope)

---

### Post by NissanSkylineN1 on 2010-05-01
Well it has been 6 months. Also, the bugs aren't assigned to anyone.

---

### Post by NissanSkylineN1 on 2010-05-02
By the way, I'n downloading openSUSE right now.

---

### Post by TheVisitors on 2010-05-02
> **NissanSkylineN1 said:**
> By the way, I'n downloading openSUSE right now.

Its a Good OS. Very stable. (my default for linux)

---

### Post by NissanSkylineN1 on 2010-05-02
How did you set up your Wifi? There's no manager. Did you use Knetworkmanager?

---

### Post by chlorinekid on 2010-05-03
check out this post for a link to the bug that suggests a fix for this problem.

most likely conflicting drivers. one set will need to be blacklisted in order to allow the other set to work correctly.

i had this problem and blacklisting the suggested drivers worked for me.

[http://ubuntuforums.org/showpost.php?p=9226251&postcount=10](http://ubuntuforums.org/showpost.php?p=9226251&postcount=10)

---

### Post by TheVisitors on 2010-05-03
> **chlorinekid said:**
> check out this post for a link to the bug that suggests a fix for this problem.

most likely conflicting drivers. one set will need to be blacklisted in order to allow the other set to work correctly.

i had this problem and blacklisting the suggested drivers worked for me.

[http://ubuntuforums.org/showpost.php?p=9226251&postcount=10](http://ubuntuforums.org/showpost.php?p=9226251&postcount=10)

Would have been good to detail this on how to "black list" in Ubuntu

---

### Post by NissanSkylineN1 on 2010-05-04
I've got a bug bieng submitted right now. It will be sent to the Ubuntu bug group. Its under "Wifi cannot connect to wpa2"

---

### Post by CoolDreamZ on 2010-05-07
I have exactly the same problem (continuously asking for WPA2 password with a realtek RTL8187). I tried a live CD of Linux Mint 9 RC! and wroked perfectly.

This is a serious regression from 8.04 and should be documented in the release notes for 10.04.

What is a mystery is that Linux Mint 9 seems to be based on the same versions of the kernel, network driver and networkmanager!!

---

### Post by CoolDreamZ on 2010-05-25
I had a similar problem with 10.04, I am using WPA2-Personal security on my wireless router and I am repeatedly asked for the passphrase. I switched to WEP security and the link worked with no problem.

I solved the original WPA2 problem by downloading, compiling and installing the Realtek 8187L kernel module (driver) version 1039 from the Realtek site [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

My conclusion is that there is a bug with WPA2 support in the RTL8187 module included in 10.04

---

