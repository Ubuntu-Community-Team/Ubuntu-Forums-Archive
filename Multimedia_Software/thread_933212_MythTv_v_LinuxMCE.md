---
title: "MythTv v LinuxMCE"
date: 2008-09-29
forum: Multimedia Software
---

### Post by leg on 2008-09-29
Title should be self explanatary really but I would like the opinion of any here who has used either or both of these products. I want to put together a home media system and my initial thoughts were with MythTv. Whilst researching the project I have come across LinuxMCE which, I have to say, sounds rather impressive.

Does any one have any opinions of either of these systems or could anyone suggest another alternative that I have not found yet.

---

### Post by tschak909 on 2008-10-01
> **leg said:**
> Title should be self explanatary really but I would like the opinion of any here who has used either or both of these products. I want to put together a home media system and my initial thoughts were with MythTv. Whilst researching the project I have come across LinuxMCE which, I have to say, sounds rather impressive.

Does any one have any opinions of either of these systems or could anyone suggest another alternative that I have not found yet.

Hello, I am one of the developers of LinuxMCE.

LinuxMCE isn't just a media center, but a smart home platform combining:

* Media
* Lighting
* Climate
* Security
* Telecom

all under one roof, with a user interface that stretches across all the display surfaces in your home, including:

* Televisions
* Tablet PCs
* Nokia Internet Tablets
* supported Cell Phones (Symbian S60, Windows Smartphone, and JAVA based phones with proper bluetooth support).

Since the problem space it attempts to unify is very large, the hardware requirements are very restrictive. We have a FAQ here:

[http://wiki2.linuxmce.org/index.php/FAQ]("http://wiki2.linuxmce.org/index.php/FAQ")

If you follow the things in this FAQ, you will get a working system :)

We have a lot of features that aren't available elsewhere, including:

* Unified control system, a wide variety of control options control everything in the house
* Legacy control of A/V gear.. control your TV, Amplifier, cable box etc.. as a unified source, and put all your remotes, including that high priced clumsy Logitech Harmony away. (Although, we can use that too)
* All peripherals are shared house-wide..tuner cards can be in any media director or the core... NAS bricks can be used for storage...You can play a DVD sitting in the bedroom media director PC in the living room, it's all unified.
* Follow me.. have your media, lighting, climate, and security settings follow you from room to room, with a variety of presence detection techniques (manual, bluetooth cell phone, RFID, etc.)
* Simple home automation with systems like Z-Wave, X-10, EIB/KNX, and more. all able to send commands, and events to every other part of the system. Nice example of this... Media director PCs have a SIP phone, that will pause what you're watching so you can answer the phone on the TV or other phone in the room. :)

And much more.

I can answer any questions you may have.
-Thom

---

### Post by leg on 2008-10-06
Yea I got that after I posted. I have to say I am very impressed with LinuxMCE but I am not sure I need/want it all. I have noticed that you have incorporated Mythtv and asterisk into your system is there any reason I couldn't start with just a home theatre and add to it over time? Could I get Myth installed and then convert at a later date?

---

### Post by scotland60b on 2008-10-31
Hi Thom (or anyone),

Hope you are still out there.  I am very interested, but intimidated by LinuxMCE.  As with some others I think it may be more than I need and right now it's a toss-up between that and MythTV.  Maybe you can help with some questions.  I would like to start with a hybrid core whether I go with MythTV or LinuxMCE, because I will likely only have one TV or media area.  However, I'd like to be able to view liveTV wirelessly.  I know that MythTV can do this by having MythTV Frontend installed.  Can LinuxMCE do this without having to reboot into LinuxMCE as a Media Director?  Ideally, I would like to have a media PC downstairs with my TV, but be able to tune at least analog cable on my monitor up in my office, and have my wife be able to tune in on her Vista laptop as well.  Could she do this using MythTV Player?  Will Web Orbiter allow her to view streaming live TV on her Vista laptop?

I have seen some older threads describing using a Treo as an orbiter.  Can my 680 do this over Bluetooth?  And I think I could also set up a universal remote with USB UIRT to work as well?  I don't care so much to set up the "follow me" thing.

Do I have to use Kubuntu?  I prefer the GNOME environment, and would still like to be able to access the desktop to use the hybrid core as necessary.

As for hardware, that is one reason I don't want to have a full fledged system with separate core and media directors right now.  I am in the military and move a lot.  I don't want to have to set up an external and internal network every time I move.  That being said, with a hybrid core is it still necessary to have 2 NICs?  That may be difficult with the SFF box I would like to use as my media center, since I only have a PCI and PCIe port...will need one for video card and one for the tuner.  

Any advice would be appreciated.  I am trying to do my homework before buying a bunch of stuff.

Cheers
Scot

---

