---
title: "HTC Hero and Ubuntu Bluetooth BlueProximity"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by nicholas.alipaz on 2009-12-22
I recently got an [HTC Hero]("http://www.htc.com/us/products/hero-sprint") and wanted to set it up with blueproximity with my laptop.

Prior to the hero I had a cheep little nokia that was working perfectly on blueproximity so I think I can attribute this to the hero alone.

Specs:
[INDENT]HTC Hero (sprint) firmware 1.5
Ubuntu Jaunty 9.04 on ASUS N70sv
BlueProximity 1.2.5
Bluetooth Applet 1.8[/INDENT]

Issues:
[INDENT]I can pair the devices, but then the phone reads "paired but not connected" under "Menu -> Settings -> Wireless Controls -> Bluetooth Settings"
I can pair the devices, but the bluetooth applet under "Bluetooth Applet Context Menu -> Preferences" shows the device as disconnected no matter how much I hit connect icon.
I can pair the devices, but blueproximity constantly connects/disconnects to the device.  It seems like it just goes between connected/disconnected each second.[/INDENT]

Does anyone have any experiences with BlueProximity and the HTC Hero, and if so were you able to get it to work?  Any other assistance?

TIA

---

### Post by puppywhacker on 2009-12-22
I believe android has extremely poor bluetooth support only usable for the audio profile (as in carkit or bluetoothheadset). I couldn't use my hero for anything else.

---

### Post by nicholas.alipaz on 2009-12-22
puppywhacker, thanks for sharing your experience.  very disheartening for sure.

Just thought I would share my communications with HTC:

[QUOTE="Nicholas"]I recently got an HTC Hero and wanted to set it up with blueproximity with my ubuntu 9.04 laptop.

Prior to the hero I had a cheep little nokia that was working perfectly on blueproximity so I think I can attribute this to the hero alone.

Specs:

    HTC Hero (sprint) firmware 1.5
    Ubuntu Jaunty 9.04 on ASUS N70sv
    BlueProximity 1.2.5
    Bluetooth Applet 1.8

Issues:

    I can pair the devices, but then the phone reads "paired but not connected" under "Menu -> Settings -> Wireless Controls -> Bluetooth Settings"
    I can pair the devices, but on ubuntu the bluetooth applet under "Bluetooth Applet Context Menu -> Preferences" shows the device as disconnected no matter how much I hit connect icon.
    I can pair the devices, but on ubuntu blueproximity constantly connects/disconnects to the device. It seems like it just goes between connected/disconnected each second.

It seems to me that there is some sort of issue where the Hero cannot hold a connection to my laptop.  Can you guys provide any hints at what might be wrong?[/QUOTE]

[QUOTE="HTC Support"]The best way to get support for 3rd party applications is to contact developer of the application Usually you can use the number listed or the email address that is provided in the actual application or on the site where the app was download.[/QUOTE]

[QUOTE="Nicholas"]Although, there is a third party plugin involved I have to say that this is certainly an issue with the HTC Hero and not the plugin. Why should the phone not be able to make a connection to my computer?[/QUOTE]

[QUOTE="HTC Support"]Dear Nicholas, Thank you for contacting HTC Support. Unfortunately, we do not support Linux devices. I apologize for the inconvenience that this may cause. Once again, thank you for contacting HTC Support. Regards, HTC Support[/QUOTE]

[QUOTE="Nicholas"]Geee, you guys don't support Linux.... Yet Android is a Linux platform....... very odd. Thanks for nothing.[/QUOTE]

I was a bit of a jerk, but the guy made zero effort so I felt it was called for.

---

### Post by puppywhacker on 2009-12-22
it's not really HTC's fault, it's that android isn't a very good mobile phone platform yet. The applications are great, but things you come to expect from a phone are just lacking. For instance, the dalvik vm is based on java, yet it is incapable of running very simple java me programs.

On the plus side, HTC will give the hero an upgrade to Android 2.0 or 2.1 which should improve things in general. So fingers crossed =)

---

### Post by misse- on 2010-04-19
Hi, 

I found this thread while googling for the exact same error. I also found this blog: [http://joepcremers.nl/wordpress/?p=1901](http://joepcremers.nl/wordpress/?p=1901) which described how to do it.

I tried to scan my device for useable channels and only Channel 1 turned up to be usable. I changed blueproximity to use that channel and since then I haven't seen that blueproximity has tried to reconnect. I'll let you know if that happens though.

Regards,
misse

---

### Post by lunatico on 2011-06-27
I know this thread is a bit old... hope people involved are still reading it.

I too have been using blueproximity with other "normal" phones and it has always worked like a charm.
But then I bought an Android phone (Samsung) and ever since I have a problem in which some times when I come back my computer won't unlock. Anyone else using it with and Android?

---

### Post by thatsenough on 2011-08-11
I also have a Samsung (Nexus S). As misse suggested, I tried to scan for usable channels and voila ! After selecting a usable channel, everything suddenly worked perfectly.

---

### Post by CaptainMark on 2011-08-21
i have no end of trouble trying to connect my htc desire to ubuntu 11.10, after it is paired then i cant get it authorise, i thought they were the same thing but when sending files ubuntu>htc i get the message 'permission denied' when trying to transfer files htc>ubuntu i get the message 'connection refused' awesome

---

### Post by jaygo on 2011-10-28
After pairing my Android phone with Ubuntu I was able to transfer files in both directions (using "send" or "share" from phone and "send to..." from nautilus). However, Android seems to block certain filetypes. I could send jpgs and zips no problem but could not send a ttf or apk.

As for using **BlueProximity**. I'm still testing to see why it didn't work out of the box, but at the moment I've got it working. I had to change the RFCOMM channel (in blueproximity preferences) to channel 12, which is one of 4 usable channels. 

While using any of the other usable channels (10, 11, 19) blueproximity didn't work, or it connected over some other bluetooth function -- using channel 19, for instance, connected to my phone's address book. If I chose to permanently allow this on the phone, the connection stayed established (which probably drains a lot of battery) and blueproximity worked.

I recommend setting your locking & unlocking times to 1 second while testing. After testing, these settings worked for me:

Locking distance: 1 or greater
Locking duration: 15 or greater (this avoids locking while the PC is establishing a connection)

Unlocking distance: 5
Unlocking duration: 1

---

