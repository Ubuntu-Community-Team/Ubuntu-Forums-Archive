---
title: "Installing Ubuntu 11.04 onto an external HDD and make it boot off it"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2011-04-26
Hi there,

Numerous hits on Google on this subject, but most of then refer to Natty -2 or even -3. Need a guide that uses Grub2 instructions and preferably for Natty.

I have done the following:
(1) Connected the external Western Digital 160GB external HDD to the laptop
(2) Booted off Live CD and asked to Install Ubuntu
(3) Selected the /sdb drive (I first created a root partition and a swap partition on this hdd)
(4) Formatted and assigned / to the large partition and assigned about 6GB to swap.
(5) Chose to install bootloader on sdb drive <--- is there where I went wrong? should I have installed it on sdb1 (root partition???)
(6) All went well; rebooted into the USB external drive (my BIOS can do this BTW)
(7) Only blank screen with mouse cursor blinking--can't boot into Ubuntu at all.

What did I do wrong? Please assist. Thanks,
S

---

### Post by mikewhatever on 2011-04-26
That looks about right. /dev/sdb or sdb should be the MBR of that hdd. Can you post the output of the [bootinfo script]("http://sourceforge.net/projects/bootinfoscript/").

PS: Natty 2 and 3? AFAIK, there was only supposed to be one, Ubuntu 11.04.

---

### Post by Wobblybob on 2011-04-26
I think the ans to 5 is yes you shuld have install grub on the boot disk. I've not tried this but you could have a look at this [[COLOR="Navy"]http://www.webupd8.org/2011/02/live-cd-to-fix-restore-grub-and-grub2.html[/COLOR]]("http://www.webupd8.org/2011/02/live-cd-to-fix-restore-grub-and-grub2.html")  which may fix the problem..

---

### Post by shuttleworthwannabe on 2011-04-26
> **mikewhatever said:**
> That looks about right. /dev/sdb or sdb should be the MBR of that hdd. Can you post the output of the [bootinfo script]("http://sourceforge.net/projects/bootinfoscript/").

PS: Natty 2 and 3? AFAIK, there was only supposed to be one, Ubuntu 11.04.

Thanks for the help.

That is Natty Minus 2 or 3 (10.04 and less)

Sorry, how do I get bootinfoscript when I cant boot into the external USB HDD? Do I do this from Live CD?

---

### Post by beew on 2011-04-26
It should work.Maybe your iso image is corrupted. I am now typing from 11.04 installed in an external drive (which is multi-boot with 5 Linuxes)

---

### Post by mikewhatever on 2011-04-26
Yep, a live cd/usb would do.

---

### Post by meanpt on 2011-04-26
> **beew said:**
> It should work.Maybe your iso image is corrupted. I am now typing from 11.04 installed in an external drive (which is multi-boot with 5 Linuxes)


How do you get five primary partitions in one hd?

---

### Post by cecilpierce on 2011-04-26
if you put grub on sdb then when you reboot it looks on the first drive (sda) so you need to select the second drive (sdb) when you start or change the boot order in the bios  to boot from sdb instead of sda at start up.

---

### Post by meanpt on 2011-04-26
Until the beta 2 I did experience a lack of hardware support and ended with a black screen without any cursor blinking.Some times during the installation heating warnings preceded faulty installations.  Since beta 2 was some graphical problems bridging the grub booting to the desktop were fixed, it installs but heats too much and the installation of the proposed ati and broadcom drivers do not overcome the heating problem yet.

---

### Post by jfernyhough on 2011-04-26
> **shuttleworthwannabe said:**
> 
What did I do wrong?Nothing. Everything was correct. It's likely an incompatibility (as previously said), probably graphics. Try a newer LiveCD (or one of the daily builds, e.g. [http://ftp.heanet.ie/mirrors/ubuntu-cdimage/daily-live/current/](http://ftp.heanet.ie/mirrors/ubuntu-cdimage/daily-live/current/) ).

---

### Post by kansasnoob on 2011-04-26
> **meanpt said:**
> How do you get five primary partitions in one hd?

You don't, you create no more than 3 primary partitions and one extended partition which can contain a lot of logical partitions:

[ATTACH]190065[/ATTACH]

---

### Post by beew on 2011-04-26
> **meanpt said:**
> How do you get five primary partitions in one hd?

I have one primary partition for Maverik's / partition (Mav controls grub), everything else is in a big extended partition and they are all logical partitions.

---

### Post by shuttleworthwannabe on 2011-04-26
I will try with a recent daily build and post back.

---

### Post by shuttleworthwannabe on 2011-04-27
Sorry guys, did not work at all. Used a fresh CDimage from the link provided (build 26-04-2011, 1PM)
(1) I placed the bootloader on /dev/sdb but did want to boot--blinking cursor only
(2) I then reinstalled, this time placing the bootloader on /dev/sdb5 (this is the / directory of Ubuntu install; sdb6 is swap)--still no luck with booting;  only blinking cursor
My machine is a Dell Vostro 3700 with Nvidia Geforce graphics card (discrete)--could this be the problem??
Do I have to tell Ubuntu where the MBR on the external USB HDD is? because this drive has never been in a Windows machine before? Do I have to install Windows on it first?

Ok, now I am getting edgy...

---

### Post by beew on 2011-04-27
It seems that your model may not work on Linux because of the hybrid graphic card.

[http://forums.nvidia.com/index.php?showtopic=193271](http://forums.nvidia.com/index.php?showtopic=193271)

---

### Post by ranch hand on 2011-04-27
> **meanpt said:**
> How do you get five primary partitions in one hd?
I have a dual HDD external enclosure with 2 320Gb WD HDDs in it.  You can have an awful lot of OS' on there.   I never had more than 21.

Not using it now as my interest in Ubuntu is about shot but it is a handy deal for testing.  You can have several nearly identical installs and test just one variable per OS.  Great if using pre-release programs on pre-release OS'.

Ran with that on all the time for 3 testing cycles using one of 2 "pure" installs (one funny add ones) as my main OS running boinc full blast (cpu as 99-100% all the time.  Rarely booted to my internals at all.

Boinc is a great way to put stress on an OS.  If it will continue to work and do what you want to do while doing that heavy duty number crunching you have a pretty stable OS.  I kept 2 OS' for my main so that I could be sure that 1 always worked.

The other installs were for, besides programs or features from ppas, Lubuntu and Xubuntu.  If you have the space you can find reasons for having a lot of installs for testing.

---

### Post by ranch hand on 2011-04-27
> **kansasnoob said:**
> You don't, you create no more than 3 primary partitions and one extended partition which can contain a lot of logical partitions:

[ATTACH]190065[/ATTACH]
Or, and I am not recommending this, you can just format your whole drive as one extended partition.  All mine are that way.

You can ruin a drive, or in my case 3, very easily doing this until you;
a>get the process right
b>come to your senses and just partition like normal folks

I stick with "a".  I like the extreme flexibility it gives me.

---

### Post by ranch hand on 2011-04-27
> **shuttleworthwannabe said:**
> Sorry guys, did not work at all. Used a fresh CDimage from the link provided (build 26-04-2011, 1PM)
(1) I placed the bootloader on /dev/sdb but did want to boot--blinking cursor only
(2) I then reinstalled, this time placing the bootloader on /dev/sdb5 (this is the / directory of Ubuntu install; sdb6 is swap)--still no luck with booting;  only blinking cursor
My machine is a Dell Vostro 3700 with Nvidia Geforce graphics card (discrete)--could this be the problem??
Do I have to tell Ubuntu where the MBR on the external USB HDD is? because this drive has never been in a Windows machine before? Do I have to install Windows on it first?

Ok, now I am getting edgy...
You do have your bios to boot from the usb devicce first?  I would double check that.

If you do, and the bugger just won't do it, run the boot info script from the live CD and send the results.

---

### Post by beew on 2011-04-27
> **ranch hand said:**
> You do have your bios to boot from the usb devicce first?  I would double check that.

If you do, and the bugger just won't do it, run the boot info script from the live CD and send the results.


It is a graphic card problem. See my link.

---

### Post by shuttleworthwannabe on 2011-04-27
> **ranch hand said:**
> You do have your bios to boot from the usb devicce first?  I would double check that.

If you do, and the bugger just won't do it, run the boot info script from the live CD and send the results.

BIOS is setup to boot from USB external drive (F12 Boot Options).

I will try the bootinfoscript--do you know how to run this script (execute) the commends in the script? In LiveCD mode, where do I save the script file? and How do I run this script?

Thanks
S

---

### Post by shuttleworthwannabe on 2011-04-27
> **beew said:**
> It is a graphic card problem. See my link.

I am able to run Natty off the USB Drive as a live USB--installed the nvidia drivers from synaptic (nvidia-current) and it boots into Unity Desktop with 3-D enabled by default.
But you may be on to something here--at boot up, get a text error message that can't find i950 graphics enabler?? or somthing likethat.

---

### Post by ranch hand on 2011-04-27
> **shuttleworthwannabe said:**
> BIOS is setup to boot from USB external drive (F12 Boot Options).

I will try the bootinfoscript--do you know how to run this script (execute) the commends in the script? In LiveCD mode, where do I save the script file? and How do I run this script?

Thanks
S
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Gets you the script and instructions on usage.

Just use FF in the Live Session and send the results text in here.

This is a really neat tool.   I keep it on my box just to get info in a hurry as to what I have where and how it is doing.

---

### Post by stoneguy on 2011-04-27
@beew - Did you try adding the *nomodeset* parameter to the kernel line of your boot stanza? Helps with some Intel chipsets, and disables Unity (yay).

---

### Post by ranch hand on 2011-04-27
> **stoneguy said:**
> @beew - Did you try adding the *nomodeset* parameter to the kernel line of your boot stanza? Helps with some Intel chipsets, and disables Unity (yay).
I didn't even think of that .  I have had to do that since 10.04 on just about every install of Ubuntu to have any chance of booting (one reason I am down to one install).  I guess I just assume everyone has to have that in their mind to boot these dogs.

---

### Post by beew on 2011-04-27
> **stoneguy said:**
> @beew - Did you try adding the *nomodeset* parameter to the kernel line of your boot stanza? Helps with some Intel chipsets, and disables Unity (yay).

 That is OP's computer, not mine. :) But he has a powerful Nvidia card, if he has to hack to disable Unity and use the Intel card that means his laptop is not really working with Linux.

Unity 3d  works fine on all computers I have tested (one of them is a 6 year old Dell D410 with Intel)

---

