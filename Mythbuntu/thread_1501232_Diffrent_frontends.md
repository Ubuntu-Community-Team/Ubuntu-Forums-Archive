---
title: "Diffrent frontends?"
date: 2010-06-04
forum: Mythbuntu
---

### Post by hylsan on 2010-06-04
Just wondered what other frontends is out there that can connect to mythtvbackend?

know XBMC works but Im looking for a lightweight frontend that would work on my ARM device.

---

### Post by ian dobson on 2010-06-04
Hi,

the backend can support upnp so any program that supports upnp should work. You don't get full frontend functionality (setting up recordings etc) but it's enough for playback.

Regards
Ian Dobson

---

### Post by newlinux on 2010-06-04
Or if you have a frontend device that can read NFS or SAMBA shares... you could use mythrename.pl to make pretty names for them to be read off a shared drive. This again would be playback only.

---

### Post by hylsan on 2010-06-04
it is mostly for viewing im after a frontend.

Read that VLC is supposed to act as a upnp-client but cant find a good guide to get it working...

---

### Post by hylsan on 2010-06-05
It seems that mythrename.pl have been replaced with mythlink.pl, but its from 10.04.

Is there a diffrence?
Can I dl the new mythlink and run on my MythTv 0.22?  where?

Thanks in advance!

---

### Post by newlinux on 2010-06-07
> **hylsan said:**
> It seems that mythrename.pl have been replaced with mythlink.pl, but its from 10.04.

Is there a diffrence?
Can I dl the new mythlink and run on my MythTv 0.22?  where?

Thanks in advance!

Ahh so it has. been a while since I used it (have full frontends everywhere now). It should work with .22 (read that on the mythtv mailing list - I can't confirm from personal experience) and .23. Of course you can still use mythrename.pl, which should be in your contrib directory if you're on a version earlier than 10.04. The options to mythlink and mythrename are pretty much the same (you can do mythrename.pl --help). I attached mythlink for you (rename to mythlink.pl and make executable).

---

### Post by hylsan on 2010-06-08
works, but cant see them on my other device even if I've shared the folder and set all to read from it. Can see other shares and i can see the folder but not the symlinks.
The folder with the actual recordings shows up fine aswell, but the folder with symlinks loads and then shows up empty.

Anyone?

edit: can see them in term on the other machine but not in vlc :(

---

### Post by newlinux on 2010-06-08
> **hylsan said:**
> works, but cant see them on my other device even if I've shared the folder and set all to read from it. Can see other shares and i can see the folder but not the symlinks.
The folder with the actual recordings shows up fine aswell, but the folder with symlinks loads and then shows up empty.

Anyone?

edit: can see them in term on the other machine but not in vlc :(

What are you using (SAMBA, NFS, SSHFS?) How do you have it setup? Perhaps you have setup options such that symlinks aren't visible or can't be followed.

---

### Post by hylsan on 2010-06-08
using samba (I think, its the built in mythbuntu 9.10 - system -> shared folders)
Just added the folder and nothing else.

So all tips are appreciated, since Im just a happy amature on linux :)

And the symlinks were created with the mythlink.pl-script.

---

### Post by newlinux on 2010-06-08
Can't say I've ever done it that way, I've always manually edited /etc/samba/smb.conf. I never used 9.10 (skipped over 9.10), but I don't see a System->Shared Folders menu. Perhaps that is something mythbuntu installs (I'm using regular ubuntu, but with mythtv installed.

Yeah, I don't think your symlinks are the problem, but perhaps the options setup in your sharing don't allow them to work when accessing the directory as a shared using SAMBA.

Can you post your /etc/samba/smb.conf file? I know that samba disabled a few symlink options by default a little while back - we may just need to reenable those. If you are in fact using samba you probably need to add:

```

follow symlinks = yes
wide links = yes
unix extensions = no

```

to the global section of your smb.conf file and restart smbd.

---

### Post by Backharlow on 2010-06-08
VLC...
Media > Service Discovery > Universal Plug'n Play discovery
then in playlist window, upnp servers show up. 
Finds someone's windows xp media server, someone else's vista media server. Also finds ushare server on a Mac. Finds tversity server on another windows. Finds ushare another Ubuntu.
Ubuntu VLC finds every assorted upnp on my network. This also works on the Mac VLC, but not Windows VLC.

Also in repo..
rygel appears to be able to hook upnp into gstreamer playback, so you could just use Totem. Neat.

there was also a simple upnp media player in 9.10, but missing in 10.04, or I've gone blind?

For non-myth servers, ushare is easy and stable.

---

### Post by newlinux on 2010-06-08
> **Backharlow said:**
> VLC...
Media > Service Discovery > Universal Plug'n Play discovery
then in playlist window, upnp servers show up. 
Finds someone's windows xp media server, someone else's vista media server. Also finds ushare server on a Mac. Finds tversity server on another windows. Finds ushare another Ubuntu.
Ubuntu VLC finds every assorted upnp on my network. This also works on the Mac VLC, but not Windows VLC.

Also in repo..
rygel appears to be able to hook upnp into gstreamer playback, so you could just use Totem. Neat.

there was also a simple upnp media player in 9.10, but missing in 10.04, or I've gone blind?


For non-myth servers, ushare is easy and stable.


I agree, if you can get a UPnP client to work, go with that. That's what I used on a third party device until a software update seemingly broke it working with myth - then I had to go to using the CIFS shares, which worked well...

Note, if you use ushare you will still want to create pretty names for myth recordings, because the filenames are strings of the channel id, date, and time - not the easiest to remember what a recording is - and that's what ushare will show.

---

### Post by hylsan on 2010-06-09
I'll check out the config-file for samba.

Sadly I have a special arm-version of vlc which dont have this 
"service discovery", so I cant use that sadly.

---

### Post by hylsan on 2010-06-09
Editing the samba.conf worked great, now I see them.

But now I cant play them...
I watched recordings yesterday, but now I get "mpgv"-files not supported.

---

### Post by newlinux on 2010-06-09
Well, at least we are getting somewhere. So where you able to play them yesterday through the symlinks? Or directly. Are you able to play them now directly (without symlinks) or not at all? What are you using to play the videos?

I don't know much about ARM devices. What are you running on it?

---

### Post by hylsan on 2010-06-09
I watched them directly, and not through symlinx, now I cant play none of them.
Using VLC. But its strange since the only change Ive done is the samba.conf.

I'll try more tomorrow.

---

### Post by hylsan on 2010-06-10
funny, but after a reboot it all works fine now. I mostly suspend it.
Now I just have to tweak up the bandwidth :)

Thanks a lot!

---

