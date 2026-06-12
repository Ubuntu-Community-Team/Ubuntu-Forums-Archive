---
title: "iPhone and Rhythmbox... what's happening?"
date: 2010-07-04
forum: Multimedia Software
---

### Post by quequotion on 2010-07-04
So I've seen all the buzz about the new libimobiledevice supporting iphone well enough to get it working with rhytmbox "out of the box".

I've achieved photo sync, internet tethering, and ssh access, but I don't know about music access.. there doesn't seem to be anything happening between rhythmbox and the iphone.

Rhythmbox regocnizes the phone and plays the music on it... but I can't seem to make any changes to that music.

The phone occasionally says "sync in progress" but I haven't pushed any "sync" button as there doesn't seem to be any or any settings for automatic syncing...

um.. what?

---

### Post by quequotion on 2010-07-08
Does anyone have more information about this? I'm going to try deleting all the music files on my iphone and try to copy files from rhythmbox again..

---

### Post by quequotion on 2010-07-08
Oh i get it  now..

It was indeed working, just not the way I expected it to.

Rhythmbox doesn't exactly 'sync' music with the iphone. libimobile device allows it to copy files to or from the device and register them in the iTunesDB on the phone.

The interface in Rhythmbox is drag and drop. There are no buttons or settings to 'sync'.

This gives me the distinct impression that I could copy files to the phone and delete the originals. iTunes forces you to keep two copies of everything and I never really liked that 'feature'.

It would be nice, in Rhythmbox, to have a context menu item like "Sync to ->" or "Copy to ->" with a sub-menu to choose PC or a mobile device.

---

### Post by quequotion on 2010-07-09
48 hours later...

When attempting to transfer my library (of about 5gb and 1200 songs) I have run in to several problems.

At some point during the transfer rhythmbox will crash,  often with a great number of blank popups (one for each transfer failure i think) and and fully freezing the computer.

After a reboot (sometimes ACPI shutdown works, but other times i had to pull the plug) rhythmbox most likely will not transfer any more music to the iphone and immediately crash and freeze again. This seems to be due to files being saved on the device (perhaps partially) without getting registered in the iTunesDB. Solution: delete everything (in /var/mobile/iTunes_Control/Music) and start over. Also, if Rhythmbox manages to crash without the computer freezing, it will become an unkillable zombie process which prevents another Rhythmbox process from running.

The most success I've had so far was to disable all network functionality on the iPhone (except usb), disable compiz in ubuntu and not touch a thing for three hours. Rhythmbox transferred three hundred songs before freezing and going blank. Metacity seems a little more resistant to freezing than compiz, but it also was frozen on several occasions. Using tethering while transfering music also seems to be a bad idea as Rhythmbox crashed twice as often while tethering and the iphone battery dies very quickly.

I'll try again with gtkpod...

---

### Post by quequotion on 2010-07-10
gtkpod doesn't do iphones.. cute...

restored library with windows. looks like i won't be getting rid of it quite yet.

---

