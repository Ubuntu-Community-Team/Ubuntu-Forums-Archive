---
title: "Streaming Media off of a server."
date: 2010-08-24
forum: Multimedia Software
---

### Post by christhegoth on 2010-08-24
As I'm sure you'll appreciate sometimes it's easier to have your music files on a samba share on another machine.  That way you can patch into your ch00n5 from all over the network.

Windows does this nicely via 'map network drive', and Ubuntu used to be able to do it via 'Rhythmbox'.  Under this new kernel I popped in yesterday it now can't.

Debian has also just released a new kernel, and once again Rhythmbox is quite happy to stream off of the server.

So Debian can do it, and Ubuntu can't.

It's also very difficult to 'save as' to a network folder with Ubuntu.  Something that is easy to do with windows.  You have to save locally, and then transfer it over to the network server.


Really this post is general feedback, but I'd say this is an area that does need work.  'Map network drive' is an excellent facility, and I do feel Ubuntu needs to catch up.  If Debian can do it better then at least you'll have something to work with.


Apart from that I'm still happy to be using Ubuntu.  I'm running Hardy Heron for the record, as I can't get Lucid in on this machine.  Driver issue by the looks of it.  I'm waiting for Maverick.

---

### Post by Ghost_Mazal on 2010-08-24
I replaced the "Map network drive" function that Windows have by adding a permanent mount point to my network share in fstab. So my share is always mounted upon system start-up and you then have functionality such as "save-as" to it.

---

### Post by christhegoth on 2010-08-24
Hmm, interesting.  What's teh code pliz?  I wasn't aware you could put an smb address in fstab.


Christian  :)

---

### Post by Ghost_Mazal on 2010-08-24
```
//serverip/sharename /mnt/app cifs username=usernameforshare,password=passwordforshare 0 0

```First create the folder /mnt/app and give your user full rights to it. (or create any other folder you want and put it in there)
Then add that line in your fstab.
After saving your fstab file execute the command sudo mount -all to test.
If no errors your share will mount there everytime your system starts

Then you can go to your share by just going to /mnt/app and use it in any application to browse or save to ;)

---

### Post by christhegoth on 2010-08-24
Yeah, I've just found that.  One problem, the passwords.

They're all in plain text, as are the usernames.  Anyone can crack open your machine, whip out yer drive, and simply read fstab to do the rest...

That's quite the fail.

What changed in this recent kernel to stop the old 'keyring' way working?   And, simply, I can haz it back?

---

### Post by christhegoth on 2010-08-24
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Has a -netdev option as well, which is handy.  But it also shows how the usernames and passwords are in plain text.  They're not hashed in any way.

---

### Post by christhegoth on 2010-08-24
Ok, now Rhythmbox won't play back.  And nor will Audacious.

Movie Player ( Xine ) gives zero sound output as well, whilst saying it's playing.  Just normal files.

Rhythmbox and Audacious can't actually see the files.

1 new kernel, and this much goes out the window.  Wow.

---

### Post by Lars Noodén on 2010-08-24
What has been described above is file sharing or sometimes called Network-attached storage.  

Streaming is a different matter usually.  There are a lot of choices out there if you search for the terms "streaming" "music" "ubuntu"

[Firefly](http://jamescanspel.blogspot.com/2009/08/setting-up-music-streaming-server-using.html) is one.  [Apache can stream](http://ubuntuforums.org/showthread.php?t=34359), too.  Icecast2 and VLC can also do music.

---

### Post by christhegoth on 2010-08-24
Cheers Lars.  I adjusted the apache2 on this machine to host the music directory for access via browser, and that works fine as well.

Yet I still can't play back.  Even with VLC.


If I hover the mouse over the file in question ( an ogg file ) it will playback through the preview option in gnome.  But nothing else will play it.

Most bizarre.  Beyond my geek-fu sadly.

---

### Post by christhegoth on 2010-08-24
Oh, and I've lost found in Flash as well.

Wipeout.

Unless Maverick supports older boards I'm gonna have to abandon Ubuntu at this rate.  I'm still on Hardy Heron due to problems I've had with Lucid.

---

### Post by christhegoth on 2010-08-24
Ah, I have Audacious back.

I reconfigured Pulse Audio using paconfig, so at least I can play ze ch00n5.  Still no sound in flash, and Rhythmbox is like a damp squid.  It just keeps locking up.

I'll leave it overnight in case it's trying to do something.

---

### Post by lopex on 2010-08-25
Why not download VLC player instead? It's probably the best free multimedia player for Windows. It supports most of the audio/video file formats out there and has all the codecs installed already. I used it for about 6 months and it has never crashed or had any bugs since that date.

---

### Post by christhegoth on 2010-08-25
Cheers Lopex.

Playback on windows units is still fine.  It's playback on an Ubuntu machine I'm having trouble with.  Which, if you think about it, is a major and very important part of a working desktop Linux system.  No ch00n5 = sucky sucky.

I shifted the media drive to the problem machine, to make it 'local' rather than a samba share on another machine, and this is how I have Audacious back.  But it's definitely a step down from previous 'performance abilities'.

Well, at least I can play music still.  That's better than the deathly silence of 'tea alone' ;)

---

### Post by christhegoth on 2010-08-26
Reply to all.


Firstly thanks for the assistance.  I've now adjusted my samba server to have a low security share username and password, and then I've only linked it to certain shares.

With passwords not hashed it should be obvious why, but this does seem to work.

So this does work.  But I would suggest Ubuntu find a way of have the username and password bit in fstab as some kind of code, and then link to a username and password in the 'users' list.  Under the keyring system, although this is beyond my own personal geek-fu.

At least then it won't be in plain text.

I've also found if you use the term '_netdev' it is dependent on the network being there as to whether it tries to mount. And if you add the term ',user' you get a nice icon on the desktop that also shows up in gnome.  Although the last ',user' bit only worked in Debian.

Also, when you create a file on this share from an Ubuntu or Debian  machine it creates it as a 'root owned' file.  So that's a lot of chown'ing if you've transferred 30 odd files.  Oh, and you have to chown the subfolder to do the subfolder etc etc.

So mass files like this are pointless really.  You might as well copy and paste from the local machine via the current samba set-up.

Thankfully you can have 2 bookmarks.  1 for the local folder 'hosting' the samba share ( /YAWN/ETC ), and another for the network share itself ( 'SHARE on BLAH' ).  Then you add bulk files via the normal network share bit ( 'SHARE on BLAH' ), and only use /YAWN/ETC for reading and writing to the odd 1 or 2.  As if you add them on 'SHARE on BLAH' you'll still have to 'chown' them on /YAWN/ETC.

Which is a bit of a headache if it's 50 odd files, and some are in subfolders.

Internal ftp will also work obviously, but may not be of use for sharing networked music folders.


So it's far from perfect unless it's the odd 1 or 2 files, like shared calendar files ( .ics on a network share ) for Sunbird for example.  Due to this instant root thing.

Now add to that the plain text issue and you're in trouble really.  Windows just does it better.  Even Debian does it better sadly.


The addy system in fstab has the IP, the username, and the password.  So if your machines are nicked all they have to do is turn on the server and workstation on a bit of cat5 crossover, after fs-tabbing by USB caddy, and they're in.  On your shares.

Yeah.  It's that easy.

I have found that, by using Truecrypt file-vaults as the addresses to be shared on the server, you still get a good response ( like a normal directory ).  The shared directory is /media/truecrypt8 ( for example ) in the smb.conf file.  But at least then, if the server is nicked, the filevaults will close on power-down.  And will not re-open on a normal boot-up.

You have to manually open them after logging in, unlike normal Samba shares ( which go straight in immediately and show everything ).  So that is some shielding at least for your data.

Plain text passwords sucky, so that does need fixing.  As does this 'root' thing.


As for my bizarre media problems?  I can see flash with sound through facebook, yet get no sound from youtube directly.  Shakespeare's Sister's webby sound works fine, but I can't get sound on my apache2 share here through the same browser ( playing oggs hosted locally ).

All of this started when the new kernel went in, so that's not really useful.  Debian still has the edge here.

And Rhythmbox is still stuffed on local files.  It just grinds to a halt.

Oh well, at least some stuff works.


Cheers :)

---

### Post by christhegoth on 2010-08-27
And a further update:

Rhythmbox is back.  I transferred the data to a more reliable drive as the original one was starting to get problems.

I also put it back on a network share as well, and mounted it like before.

There's a new kernel waiting to go in this morning, which I have not installed yet, and Rhythmbox is back and happily reading off the network.  Like before.

I'm getting bad I/O errors on the drive, so looks like it's on its way out.  It vibrates like a bugger as well.


So I learned something new with this 'mount network share' stuff anyway, and got Rhythmbox back.  Winnar :)


And now to put in the new kernel...

---

### Post by christhegoth on 2010-08-27
And with the new kernel Rthythmbox is now unreliable...

It can see the files, but won't play 'em.  It says it's a bug in gstreamer but even so.

Still no sound in flash with Youtube sadly, but it works via facebook.  Which would also suggest gstreamer.

Bugger.

---

### Post by christhegoth on 2010-08-27
Oh, and if your 'smb share mounted in fstab' is goes offline for too long the workstation crashes as well.

As I just found out.

Yup, needs some work.  But if they can crack it that would be very handy indeed :)

---

### Post by christhegoth on 2010-08-30
One last update.

The drive was not failing. It was a gammy power cable.  So that share on the server is back up.  It is also read only, which is how I normally do things with the music share.  That way you can't accidentally delete your music collection.

To do any editing of the music share and it's contents you need to log in with an ftp client.  And update it that way.  Obviously, this is pretty safe.

The read only share is also safe to have on this lower security plain text system, as it's just music.  And it will mount on the fstab edit.  So that's it solved really.

Gnome Commander has a decent bookmark system as well as an ftp option for the right pane.  So you can still 'browse and edit' IYSWIM in an interface that is like Gnome's normal option.  But without that ftp log-in you can't tamper with it.

And that's the secure bit.

It seems to be a good reliable work-around, although there is still a risk of workstation crash if the server is turned off for some reason.  You might as well have just unplugged a system drive, whilst the workstation is still on, for the instability it creates.

If they can crack that last bit, and the instability problem, then I'd say we're almost at 'problem solved'.  After that it's just that pesky chown'ing problem.  And that is bypassed by the above as well.

Once the system crashing problem is solved I might even roll out Rhythmbox again.  At the minute I'm just using Audacious.

---

