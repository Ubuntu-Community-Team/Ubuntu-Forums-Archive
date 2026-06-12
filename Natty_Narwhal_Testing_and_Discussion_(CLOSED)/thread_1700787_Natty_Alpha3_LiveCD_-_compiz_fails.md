---
title: "Natty Alpha3 LiveCD - compiz fails"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mechanic on 2011-03-05
I get a 'compiz failed to start' message box, then no desktop or panels or right-click menus. WTF? I can exit using Cntrl+Alt+Del and switch consoles using Cntrl+Alt+Fwhatever, and I can see processes like X, gdm are there but nothing on the screen. I can even call up the help window on the shutdown screen, but that's not much use.

Any boot parameters to add (but I can't see how in the boot process)?

Any other tricks to get a desktop up?

---

### Post by EowynCarter on 2011-03-05
I'm feeling less alone sudenly :)

I have the exact same symptom on my eeePC. (1001px).
What computer are you using ?

---

### Post by jerrylamos on 2011-03-05
> **mechanic said:**
> I get a 'compiz failed to start' message box, then no desktop or panels or right-click menus. WTF? I can exit using Cntrl+Alt+Del and switch consoles using Cntrl+Alt+Fwhatever, and I can see processes like X, gdm are there but nothing on the screen. I can even call up the help window on the shutdown screen, but that's not much use.

Any boot parameters to add (but I can't see how in the boot process)?

Any other tricks to get a desktop up?

Compiz crashes for me (Compiz has been crashing regularly starting in Intrepid and every Ubuntu since) so I do a Ctrl-Alt-F1 or whatever to get a command line, then:
sudo service gdm stop
sudo service gdm start
wait a bit...Unity might come up...

I've entered a number of launchpad bugs on Compiz crashing on start on two pc's that run Unity 3D.  So far no action.  There's presumably a new kernel 38-7 coming along; I'm running 38-5.

Jerry

---

### Post by mechanic on 2011-03-05
This is too strange - I tried the Alpha3 live-CD on another machine with a decent 3D video card and all I could get was the standard Gnome desktop and panels. Back to the first machine which is an old Dell Dimension 9150 (?) with on-board video and which often fails to run compiz but for once it started without complaint and showed the Unity desktop!

Time for a lie down...

---

### Post by cariboo on 2011-03-05
The only graphics adapter that will allow you to run Unity from the live CD is Intel, Nvidia and ATI/AMD need extra drivers installed in order to run it.

---

### Post by jerrylamos on 2011-03-05
> **cariboo907 said:**
> The only graphics adapter that will allow you to run Unity from the live CD is Intel, Nvidia and ATI/AMD need extra drivers installed in order to run it.

?  This post is from CD Live on ati radeon xpress 200 with Unity 3D running with all its features  and warts....As I remember from a couple days ago when running from USB stick Unity 3D was up as well, I can check that if anyone is interested....

Now this is a multi boot and there is a partition elsewhere that has Natty installed on it.  It's not mounted according to terminal command line: 
df

Jerry:confused:

---

### Post by azurehi on 2011-03-05
> **cariboo907 said:**
> The only graphics adapter that will allow you to run Unity from the live CD is Intel, Nvidia and ATI/AMD need extra drivers installed in order to run it.

I require Nvidia 96.  Compiz crashes when trying Natty Alpha 3.  Were I to install would I be able to use Synaptic to install Nvidia 96 (I could install Nvidia 96 in 10.10 but flicker was terrible...using 10.04.2 presently).  Maybe my video card is just too old (?).

---

### Post by cariboo on 2011-03-06
@jerrylamos, I'm only going by my own experience, the only system I own with an ATI graphics adapter is older then your systems, so I won't even bother trying to run Natty on it. My netbook with 945 graphics chipset runs Unity out of the box on a live usb device.

@azurehi, I'd suggest you check directly with nvidia to see if the 96 driver has been updated to work with the latest Xorg-xserver. We are using version 1.10 for Natty.

---

### Post by EowynCarter on 2011-03-06
Maybe in live CD mode, it would be nice of the user to be able to say "start gnome panel".

Edit : I tried again this morning, indenting to try the "Ctrl-Alt-F1" thing. And, guess what, the netbook happily started unity without my having to do anything. 
/Me is perplex. I tried 3 times yesterday without any success...

Re-edit : After a really shot while using the netbook, compiz crashed.

At least it's encouraging. It **can** work. Just some stability problem rather than "won't work"

How much ram do you have on your machine ? I'm wondering if that's not caused by lack of enough ram to run on live usb.

---

### Post by mechanic on 2011-03-06
> **cariboo907 said:**
> The only graphics adapter that will allow you to run Unity from the live CD is Intel, Nvidia and ATI/AMD need extra drivers installed in order to run it.

So which bug is that exactly? I don't see a reference in the release notes, but I may be overlooking the obvious!

And I see from listing my pci devices that this machine has an ATI Radeon X600 card (too easy to loose track when you swap these things around a lot!).

When are we expecting support for these ATI devices to emerge?

---

### Post by jerrylamos on 2011-03-06
> **EowynCarter said:**
> . It **can** work. Just some stability problem rather than "won't work"

How much ram do you have on your machine ? I'm wondering if that's not caused by lack of enough ram to run on live usb.

Eowyn, the Aspire netbook running Unity 3D has 1 GB ram.  It's also got 250 GB hard drive which I have split between Maverick (quick) and Windows 7 starter (slug).  Natty is happily running off a USB Hard Drive - old 36 GB notebook hard drive in a USB adapter.

Intel Corporation N10 Family Integrated Graphics Controller has had some Conmpiz crashes of course since Compiz's main effect for me is to crash.  I run full screen applications internet, write, ... so I hardly ever see any "shading" or "3D" or anything other Compiz "eye candy".

With F11 full screen I get a really usable screen in 1024x600 without any borders or other real estate wasters.

Jerry

---

### Post by P-I H on 2011-03-06
> **cariboo907 said:**
> The only graphics adapter that will allow you to run Unity from the live CD is Intel, Nvidia and ATI/AMD need extra drivers installed in order to run it.

I have an AMD Radeon 5450 card and this works fine with the open source driver. With "Try Ubuntu" the Unity interface starts OK. The installation works fine. VLC plays videos without tearing.

---

