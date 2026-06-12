---
title: "Can't get Lucid to Mount/Sync iPod Touch"
date: 2010-05-31
forum: Multimedia Software
---

### Post by waveslider on 2010-05-31
I just recently read that Lucid Lynx now has built-in support for syncing iPods/iPhones with Rhythmbox, which is nothing short of pure awesomeness, in my book.

When I tried to sync my 2nd generation iPod touch with Lucid, though, nothing happened. Nautilus did not give any indication that it had been mounted, nor did Rhythmbox.

Am I missing something? Like a configuration step? Can anyone help me get it to sync?

Thanks in advance!

---

### Post by djstancho on 2010-06-02
I am having the same issue can someone please help us

---

### Post by djstancho on 2010-06-02
update: i think there's an error that happens during the mounting hence the issues. when mounting the ipod ubuntu simultaneously starts rhythbox which causes the error and even if you try to re-mount it won't work. at least thats my situation and i think it's slightly different then your, waveslider. i was able to mount properly before but since recently this issue has arised. i started rhythmbox before i mount the ipod and i am to see full details on it when i click properties in rhythmbox and i am also able to sync and transfer songs. i hope that helps somehow

---

### Post by waveslider on 2010-06-02
yes, djstancho, my situation is different - i have tried to get it to work after starting Rhythmbox, before starting it, etc. It doesn't appear to be mounting the iPod at all.

I'm not sure which log file to check or what to look for  in order to determine what the problem might be. Can anyone help us?

---

### Post by smittie46 on 2010-06-02
I Dont know but for me it was that I was using a usb extension and when I plugged directly into motherboard or case usb port  everything went great also I install ntfs drivers not sure if that help but I did it all at same time so I hope it helps or leads ya in right direction Good luck

---

### Post by kelocena on 2010-06-03
Well, I haven't had a problem with plugging in my iPod and being able to listen to the songs on it via Rhythmbox. But, I've never been able to edit the contents of my iPod or sync it through Rhythmbox.

Instead I use an application called gtkpod iPod Manager to manage my iPod and edit playlists, add songs, etc. The only downside is it doesn't let you listen to the songs as you create the playlist. But I think you can import playlists from apps like Rhythmbox.

I, too, wish to get to the bottom of this.

---

### Post by waveslider on 2010-06-03
@smitty46

Thanks for your suggestions. I have my iPod touch plugged directly into one of my computer case's usb ports and also have ntfs installed, but to no avail.

---

### Post by fosezzle on 2010-12-29
All I got when I plugged in the 2nd gen iPod touch was a mount on the desktop containing only the "DCIM" folder.

libimobiledevice was installed but I didn't have all the dependencies listed on [http://www.libimobiledevice.org](http://www.libimobiledevice.org) :

ifuse
libplist
usbmuxd
nautilus-ideviceinfo (I actually still don't have this installed)

I used Synaptic to install these packages, rebooted, and the iTouch was mounting correctly after that.

However, I'm still having syncing issues. Can't seem to get music transferred to the iTouch to show up.

---

