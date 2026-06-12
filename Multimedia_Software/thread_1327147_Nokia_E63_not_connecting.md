---
title: "Nokia E63 not connecting"
date: 2009-11-15
forum: Multimedia Software
---

### Post by ak123 on 2009-11-15
I'm a relatively new ubuntu user having switched from windows when Karmic was released... im also a nokia E63 user.. the only problem ive experienced with either of them is when ive tried to connect my phone to ubuntu...

i didnt even bother trying PC Suite mode since i know there is no Nokia suite for linux

i tried media transfer (MTP) mode... that wasnt detected.. so i saw a command 'MTP-detect' in one of the threads.. that didnt work either... then when i tried to unplug the phone a few strange things happened... the phone didnt register that it had been unplugged... when i tried to connect to the internet from the phone, it gave the system error message and hung... 

the same thing happened in mass storage mode.. except this time i couldnt access the memory card

here are the things i wish to do when connecting the phone in order of importance...

sync music
manage photos
manage files and docs
sync contacts


any help would be very appreciated.. i have no issues with using terminal code as long as it will get my device to work.. i am using a desktop so no bluetooth..

---

### Post by suyog on 2009-11-24
You need to use PC Suite mode for using you phone as modem, Sync.

For syncing music, you need to use Media Player mode(in my N82) but I think Eseries phones do not have that option. right? When I select Media Player Mode , Rythmbox automatically detects phone.

For Managing photos, you need to select image print mode. Then F-spot detects your phone and can import photos, just like Image store app in Nokia PC suite in Windows.

Could you let me know which option for connection you get? so that I can help you more.

For Syncing contacts, calendar, todos , please following link.

[http://ubuntuforums.org/showthread.php?t=260676&highlight=Nokia+Sync&page=17](http://ubuntuforums.org/showthread.php?t=260676&highlight=Nokia+Sync&page=17)

---

### Post by thomaszmark on 2009-11-24
Yeah, My Nokia E63 can't work, any advice. tks

---

### Post by forest555 on 2009-11-24
Use Jaunty. 
With Karmic you are not able to sync Evolution with E-series Phones anymore. You can write only from phone to Evolution. It is a bug, I hope not forever...

---

### Post by ak123 on 2009-11-24
> **suyog said:**
> You need to use PC Suite mode for using you phone as modem, Sync.

For syncing music, you need to use Media Player mode(in my N82) but I think Eseries phones do not have that option. right? When I select Media Player Mode , Rythmbox automatically detects phone.

For Managing photos, you need to select image print mode. Then F-spot detects your phone and can import photos, just like Image store app in Nokia PC suite in Windows.

Could you let me know which option for connection you get? so that I can help you more.

For Syncing contacts, calendar, todos , please following link.

[http://ubuntuforums.org/showthread.php?t=260676&highlight=Nokia+Sync&page=17](http://ubuntuforums.org/showthread.php?t=260676&highlight=Nokia+Sync&page=17)



Thanks... but the problem is  that the phone wont get detected in any of these modes...

---

### Post by suyog on 2009-11-24
@forest555 , for me sync is working well in both directions. I am able to see add/delete/updates in both directions.

@ak123, Are you able to get it working in windwos with PC suite?

check with lsusb command in terminal if any thing related to nokia is showing up. or if you are paired with bluetooth check if you are able to browse phone memory/memory card from pc. then you may try to use sdptool browse from terminal.

Let me know it works.

---

### Post by ak123 on 2009-11-25
> **suyog said:**
> 
@ak123, Are you able to get it working in windwos with PC suite?


Yes it worked in windows with all modes except music player because of an issue with my drivers...

thanks for the tip.... will let you know if it works...

---

### Post by ak123 on 2009-11-25
> **suyog said:**
> 

check with lsusb command in terminal if any thing related to nokia is showing up. or if you are paired with bluetooth check if you are able to browse phone memory/memory card from pc. then you may try to use sdptool browse from terminal.

Let me know it works.


Okay... When i Used the lsusb command, my phone showed up... but when i tried to use sdptool browse command it said inquiry failed.... by the way.. im usin a desktop computer.. so no bluetooth

---

### Post by suyog on 2009-11-26
I think you need to find out details about your USB connection.

User following sudo syncml-obex-client -u in terminal and look for interface value for SYNCML-SYNC.

in Multisync, syncml-obex-client you need to only specify interface value which you will get from above and connection type as 5 for USB.

Please connect in PC Suite mode. Let me know how it goes.

Following links could be useful for you.

[http://cookerspot.tuxfamily.org/wikka.php?wakka=MobileSymbianSynchroMsynctool](http://cookerspot.tuxfamily.org/wikka.php?wakka=MobileSymbianSynchroMsynctool)

[http://www.opensync.org/ticket/627](http://www.opensync.org/ticket/627)

[https://libsyncml.opensync.org/wiki/obex-guide](https://libsyncml.opensync.org/wiki/obex-guide)

[http://dburr.veritel.com.au/nokia/](http://dburr.veritel.com.au/nokia/)

[http://linux.die.net/man/1/syncml-obex-client](http://linux.die.net/man/1/syncml-obex-client)

---

### Post by forest555 on 2009-11-30
Is there any news in Karmic? It is still impossible to sync from Evolution to e-series phones. 

And it works in Jaunty, Intrepid, Feisty etc. What is different in Karmic?

---

### Post by ak123 on 2009-12-08
@suyog... many thanks... ive gotten contacts and  calendar onto my phone.... however the thing i need most is still not working... my music still cant be transfer... and a gui option for that would be preferrable...

---

### Post by suyog on 2009-12-11
@ak123, Great news, how did you do it finally? could you post details? May be on your blog, if you have?

It will be useful for others here , as i guess you did via Cable.

For Music transfer, I guess you MTP connection mode should do it.
But there seems to be issue with Eseries phones, especially older.
You can have a look at this post and comments there.

[http://www.davidgilson.co.uk/2009/10/a-guide-to-linux-and-series-60-phones/](http://www.davidgilson.co.uk/2009/10/a-guide-to-linux-and-series-60-phones/)

---

### Post by melb on 2010-01-03
I've got the same problem with the E63.

My other mobile, a Nokia 6220, automounts fine with 7.04 Fiesty and 9.04 Jaunty. But, new E63 doesn't mount in either release.

Syslog shows a "hal udi" entry for ".../storage_serial_E63_...", but then nothing else happens. For the 6220c, the log shows ".../storage_serial_S60_...", which is a generic S60 entry, then it shows a mount for /dev/sda1. I suppose the fault is that the E63 is identifying itself exactly, and that Linux doesn't know abount this device!?!

I've tried to manually mount it, but no joy. There is a /dev/sda created but not a /dev/sda1 - beyond my knowledge as to what's happening.

Really, really, want this to work as otherwise no large file transfers!

Mel

---

### Post by suyog on 2010-01-04
@melb I am sure you are using Data Transfer Mode. Did you try to restart both phone and PC, just to check :)

---

### Post by melb on 2010-01-04
suyog, 

Only mode choices on E63 are "PC Suite", "Mass Storage", "Media Transfer" and "Connect PC to Web". "Mass Storage" works fine on my other Nokias - 6233 ( S40 ) and 6220c ( S60 ). But as everyone else is reporting not with the E63. I've tried clean start situations, and the other non-obvious connect modes.

Are you questioning this because you have connected an E63? If you have I'd like to know how, please?

Mel

---

### Post by suyog on 2010-01-05
@melb , I have not tried E63 connection so I am not aware if this is general issue. If you think this is general issue then please report bug via launchpad.net.

---

### Post by ak123 on 2010-02-28
hey everybody... I found the solution... It was laughably simple...

all you have to do is update the phone's firmware with a windows machine.. it works in mass storage after this... 

However.. one problem that occurs when you do this is that the phone can no longer read the memory while connected... 

result... any apps/ themes installed on the memory card cease to work...

another thing... the phone still acts up when disconnected... usually requires reboot to set it right... but its a start...

---

### Post by suyog on 2010-03-06
@ak123, Congrats, its nice to know that Firmware update has fixed the issue. It's always good to have latest firmware on phone. Problem with E63, N82 and many older Nokia phones is that we need to have either Nokia Software Updater or OVI suite on Windows Machine to update firmware. New phones from S60 3rdFP2 onwards can do OTA update from phone only.

Also the issue that you cant access memory card contents, apps while phone is in Mass storage mode -- Thats known thing and in fact good in some ways as it doesnt allow changes in both places which can corrupt files/data in card.
keep sharing your issues/experience. Hey you can check my blog also
[http://mobileyog.blogspot.com](http://mobileyog.blogspot.com)

---

