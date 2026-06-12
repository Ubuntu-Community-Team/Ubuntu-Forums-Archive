---
title: "Help with Rio Riot MP3 player on Gutsy"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by brundlelinux on 2008-01-03
Okay guys... I got a Rio Riot as a Holiday gift.  If I had been given a choice, I would have picked a player that was a bit more compatible with Linux out of the box, but I wasn't, so.....

I can't get the thing to be recognized.  It won't automount at all, although my configuration is set up to automount media at connection.  I *think* I  have the USB mass storage enabled in my kernel because  I have had several other players (of different brands) work perfectly (or as perfect as they are going to on Linux, anyhow) to include both hdd and flash based players with minimal tweaking except for the basic interface applications (Gnomad2, Ipodder, etc).  And I have never had an issue with pen drives or digital cameras either.

I've searched through all the Linux apps I can find on this and none of them work.  I started using rioutil, which is a command-line interface.  It was a bit sketchy, with minimal forward progress.  Out of any ten times I try to access the device, 7 times will result in "device not found", 2 times will result  in "couldn't resolve usb handle", and maybe once it will actually list the music tracks on the device, but not let me upload, download, transfer, or delete, instead reverting to one of the error messages.  There doesn't seem to be any rhyme or reason to this.  It does it both as user and as root.  It just seems to randomly pick which error to give me, even if I just try it time after time after time without changing anything.

I also compiled and installed Jrioutil, which is the GUI frontend for Rioutil.  It works perfectly, but again, will only return "device not found" errors.

I thought that I would just have to set up an automount script in fstab, but searching through my filesystem, it is not there to even give it a mount point.  I checked in /dev as well as /media and anywhere else I could think to look.  You would think it would be sda1 or 2, but nothing there.

However, if I pull up my hardware information from the preferences tab on my taskbar, it is listed with correct info.  It also shows up when I "dmesg" from the command line.

My box is a Sony Viao desktop.  I'm NOT going through a hub, but rather, straight in through the front USB ports.  So it's not a hub issue.  I have connected it to a Windows box, and it works perfectly there, so I know it isn't a device issue.

I've been using Linux for less than a year, and I am NOT a guru by any means.  I would LOVE some help, but please, try to use plain english and walk me through it step by step.  MANY thanks in advance.

---

### Post by angrboda on 2008-02-13
Greetings!

Ok. I just came across your post and thought I might as well try and answer some of your questions (hope its not too late).
First of all: the riot is _not_ an usb mass storage device (and I've been mourning that for sometime myself). Unfortunately that means, you will have to use a tool like rioutil to communicate with it.
Things are being complicated by the fact, that newer versions of rioutil rely on usbdevfs and thus can only work when called as root. Due to that limitation using the Jrioutil will most likely never find the riot as it would be very unsafe to have jrioutil call rioutil as root.
But do not despair: the command-line version is relatively stable and easy to use, once you get used to its little oddities. One of which is the fact, that (at least in my system) it will only work once per connection. Everytime rioutil did connect to the riot, I have to unplug and reconnect the usb for it to work again - don't ask me why this is.

Another thing is that it uploading a large collection (like mine) can be a right pain, if (as most people will do) you keep your music organized in subdirectories, as the upload-command will not descend into subdirs. Which problem is rather aggravated by the above problem with the reconnect. So unless you feel like writing scripts it might be a good idea to copy all your mp3 files into one dir and then upload it in one go via

```
sudo rioutil -b *.mp3
```

(see```
 man rioutil
``` for more options if you havn't already done that)


Afaik there is only one other linux util working with the riot. Its called riotware. If you are not afraid to compile it yourself you can find that here:

[http://riotware.sourceforge.net]("http://riotware.sourceforge.net")


riotware has the advantage of being able to descend into subdirs for upload (upload all files even if they are in subdirs) but the disadvantage of being rather unstable and also discontinued, it seems.
Just one last hint: Do yourself a big favour and make sure that all your files have a good id3 tag (eg using easytag) -- the riot is a bit touchy with bad tags and you have to go on an epic search before finding mis-tagged files on the riot.

hope that helps.
                 angrboda

---

### Post by brundlelinux on 2008-02-13
Thank you VERY much for the great info and plain English speak.  I had actually given up on this and stuck the Riot in a closet to collect dust.  I pulled it out and tried this, and it was perfect.

The only issue I have now is one of severe luxury.  My digital music collection is well over 75 gigs.  Thanks to Amarok and it's super-de-duper intuitive features, all these files are sub-divided by artist and album into a distinct heirarchal folder structure AND have fully correct track tags.

For the record, this is all 100% legal music.  I have a personal cd collection upwards of 2,000 cds.  I'm a musician and big into music, obviously.

There is NOT going to be a day where I sit down and transfer tracks one by one from the command line.  That's just absurd.  What I really need is a GUI frontend that works and allows me to pick and choose tracks to transfer.  Ideally, it would be great it Amarok recognized this player and allowed me to work directly from there.  In my situation, my collection VASTLY overshadows the capacity of the player, so just having everything in one directory and doing a bulk transfer is not a workable solution.  Especially since I would like to switch up the library on the device on a regular basis (usually weekly).  

Of course, I could just go through and make a redundant directory and pick and choose files to move into it for a bulk transfer, but again, the effort / time is insane.  This is Linux.  How is it that something as popular as music and portable players has been so overlooked in the OS for the people, by the people?  I hate to say it, but Windows at least, has this aspect of computing down better than Linux.

---

### Post by angrboda on 2008-02-13
Wow. 75 gig ? ...that is a lot of files. I had only about 15 GB  to shove over to the riot and I hated moving those... I still use the riot quite often and so I'll probably keep searching for a better solution myself. Should I find anything, I'll try and remember to post it here, so you might want to keep an eye on this thread ... no promisses though - I am rather busy ...and also, I am sorry to say,  a rather negligent writer ;-)
There is one idea I had though which I will most likely not have the time to test at the moment:

In the README-file of rioutils sources it says, that it can be build libusb-only. (set a --without-usbdevfs-flag for configure):

```
% ./configure --without-usbdevfs
```

that might make it possible to run rioutil non-root and thus eligible for use with Jrioutil.
however that would require you to create the device-nodes etc. yourself. (refer to the README in the rioutil sources for details if you are interested...)

Since my riot does hold all my music, I will not need the tool very soon or very often, so trying that out is not really a top priority with me right now...
Good luck then and happy rioting ;-)
                  angrboda

---

