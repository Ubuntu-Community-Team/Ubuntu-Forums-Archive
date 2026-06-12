---
title: "Manually installing codec plugins?"
date: 2009-01-19
forum: Multimedia Software
---

### Post by thebullfrog on 2009-01-19
Hey guys, need some help. I just got an old comp running for my GF since her laptop died. I just set it up with Ubuntu (latest version) and all is well. I need to get Rhythmbox to play MP3. I know I could DL the plugins directly, but theres a problem: The comp in question has no internet access, therefore I can't DL and install the necessary plugins directly. I need to DL them onto my laptop then transfer and manually install them onto her comp. I'm VERY new to Linux (this is my first day with it in fact lol). I've done a lot of googling but haven't come up with any clear answers. I found the plugin modules on the GStreamer website, but don't know how to even begin installing them from the source codes they have available. How can I go about getting her comp to play MP3, DVD's etc, without being able to download anything directly? Thank's for the any help in advance, been wanting to learn Linux for a long time.

---

### Post by mc4man on 2009-01-19
Being new to linux I'm not sure if this is going to be as easy as it would if you had some time in.
There would be 2 prerequisites so I'll post those and if your good I'll give you a step by.
You'd need a usb flash (thumb) or external drive with some decent free space. If you want to do dvd playback with a player like vlc and the music plugins and libs, ect.(whatever you want), then figure a couple of hundred Mb. min.

Also you'd need to ck. if your laptop (or any other pc handy with an internet connection) can load up the ubuntu live cd you used to install with on your gf.'s pc.
Also ck. that you can use the usb drive on her pc.

To ck., boot up with the ubuntu cd in and choose 'try without installing'. If you can navigate about, see everything on the screen and go online  then your good to go.

Let me know.

---

### Post by cariboo on 2009-01-19
I would suggest that you clean out /var/cache/apt/archives then go to Synaptic package manager and select the ubuntu-restricted-extras for installation, when you clcik apply there is an option to download the files only. To clear the package archive in a terminal type:

```
sudo apt-get autoremove
```

and just in case something gets missed:

```
sudo apt-get clean
```

Once all the files are downloaded you can burn them to CD and use sneaker net to install them.

THe ubuntu-restricted-extras meta package includes codecs to play most types of audio/video media, except for DVDs.

Jim

---

### Post by thebullfrog on 2009-01-20
Wow is this an active forum lol. Anywho.

Flash drive is no problem. I've got a 4 gig drive and it does indeed work on her comp. As for the Live Cd working on my lappy, I haven't tried it (and don't have it with me) but I can't see any reason why I would have any problem running it.

As for Cariboo's suggestion I'm not sure what sneaker net is if you could point me in the right direction. Not sure it would work anyway since I discovered another problem. I can't run anything at all from a disk. I can read the data but not do anything with it. I always get 1 of 3 errors: Can't find program, Don't have permission, or The file is not a .ZIP file. Any time I try and run ANYTHING off of any disk I get one of those three errors. I can use music CD's, but nothing else will run. Trying to use autorun results in either the Can't find program, or Don't have permission errors, and clicking an .EXE (or anything else for that matter) throws me the "Not a .ZIP file. Can't find the end of the central archive" or some such thing. I know it's not a .ZIP. It's an .EXE......

---

### Post by noriek on 2009-01-20
Just to address the permissions issue on the drive:

I find it easiest just to create a root account and use that for copying from external drives, i understand there is another method but this works for me.
At console, type:

sudo adduser root

(give password when prompted)

then:

sudo passwd root

create password for root and then verify it. 

Now type:

su root

and give the root password at prompt. Now you can move and copy files with ease.

As for the zip issue: i understand that ubuntu doesn't support the latest zip algorithm from default install. You can add this support from the one of the packet managers I believe but that's all i've got on that, I know it's covered on the web elsewhere tho so a search along those lines should help.

Hope this is of some help.

---

### Post by thebullfrog on 2009-01-25
No, you misunderstand. It handles ZIP files perfectly fine. In fact ZIP files are the ONLY files it will handle. Any other type of file I try and run it complains about it NOT being a ZIP file.

I may just drag her entire comp over to my parent's house (we can't afford internet ATM lol) and just download everything I need that way. Kind of a PITA but whatever, so long as I can get all of it's issues resolved it may be worth it.

---

