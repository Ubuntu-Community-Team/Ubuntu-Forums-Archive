---
title: "MTP/Windows Media Player-compatible MP3 players and Feisty"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by glittalogik on 2007-05-17
Here's how to do it, no compiling necessary! Works 'out-of-the-box' with the right packages.

I screwed around trying to get my Philips GoGear HDD6320 talking to Edgy for months with no luck, but Feisty makes it easy =) This should also work for the Creative Zen and any other player designed to work with Windows Media Player.

Noobs: just cut and paste the code bits below into a terminal window one at a time.

Ensure that your repositories are up to date:
```
sudo apt-get update
```

Install MTP:
```
sudo apt-get install libmtp5
```

Connect player to your computer.

Check that MTP can detect your player:
```
mtp-detect
```

If it spews out a bunch of info about the player, you're good to go:

Install Amarok with Xine and MTP support:
```
sudo apt-get amarok amarok-engines amarok-xine
```

Open Amarok.
Click Settings > Configure Amarok > Media Devices > Add Device.
Select 'MTP Media Device'.
Enter name for your player.
Leave mount point field blank.
Click 'OK'.
Click 'OK'.
Click Devices tab on the bottom left.
Select 'MTP Media Device'.
Click 'Connect'.

You can now transfer and edit tracks and playlists!

Notes:
- It's buggy, so don't expect seamless integration, but it works, and it beats shelling out for a new player.
- Amarok may become crashtacularly unstable whilst transferring tracks, do small numbers of files at a time to minimise issues.
- Amarok will transfer ID3 tags and album art with tracks. Ensure tags and album covers are accurate and up to date before moving them over.

---

### Post by toasterofirony on 2007-05-17
I'm intrigued why you'd want a new repo to add to your list, when you can do all this with the main repository. libmtp, Amarok 1.4.5 and Xine.

Also, I don't know if it is relevant, but I've not had any issues with crashing (even when I transferred 18 gig of music from my Creative Zen Vision: M)

---

### Post by lzfy on 2007-05-17
Thanks this works :)  But as toasterofirony said, you don't have to install any extra packages since they all are installed by default.

---

### Post by glittalogik on 2007-05-17
You are right! I got this method handed down to me and never checked that out :p

OP fixed =)

---

### Post by Jilbert on 2007-05-22
im running behind a firewall. how can i update my repository list?

---

### Post by GoLoGo on 2007-05-31
Is there an alternate player for 6.10 on the GNOME environment, or can Amarok be installed with out the KDE environment?

---

### Post by glittalogik on 2007-05-31
Amarok can be installed in Gnome, that's how I've got mine. However, its awesomeness compared to Rhythmbox has got me half-convinced to give the rest of KDE a go too next time.

---

### Post by CasperN on 2007-06-02
Hi I have a creative Zen vision M 30GB.
it works fine for me to connect the player whit amarok in gnome, I can send mp3 files and edit playlists, but I can't send any movie files to the player, anyone who have the same problem or know how to fix it? maybe if the zen can be mounted in /mnt or something?

---

### Post by ntetreau on 2007-06-04
you can install gnomad2 and transfer any kind of files

Nic

---

### Post by viciouslime on 2007-06-04
> **glittalogik said:**
> Amarok can be installed in Gnome, that's how I've got mine. However, its awesomeness compared to Rhythmbox has got me half-convinced to give the rest of KDE a go too next time.

Don't be fooled :p

---

### Post by Skerit on 2007-06-10
What a letdown, the libmtp in the repository's don't seem to do *anything*, when I install libmtp from source, an older version, and I try a mtp-detect, my phone lights up like a christmas tree and it STILL says it can't find anything ... This is getting ridiculous :(

---

### Post by glittalogik on 2007-06-10
What model phone is that?

---

### Post by kfir_w on 2007-06-15
Hi,
I'm using Creative Zen Micro on Ubuntu 7.04.
MTP doesn't recognize the player:

[I]kfir@zalame:/$ mtp-detect 
No MTP devices.
No devices.[/I]

How do I get it to work??

---

### Post by DiaperJe|\|i3 on 2007-06-20
After trying various guides and how-to's I've finally gotten the mtp plugin 1.5 to work in amarok 1.4.5 by upgrading to Feisty and using the repos. However, its damn crashtacular! If I transfer one file at a time I'm usually ok but get "random failure: unable to write to .... errors" then after 2-4 songs being transfered amarok goes greyed out and either just churns away (defunct) or just flat out crashes. Its irritating when it takes like 30 minutes to tranfer one album. If I do a whole album at once it only does the first song in the playlist then give me the same "failure to write to ..." error. Am I the only one? I understand its open source and nothing guarenteed but damn this is frustrating. Especially since Amarok is so amazing otherwise. 

Player : IRiver H10 20G (North American model)
Amarok : v1.4.5
libmtp : v1.5
OS : Ubuntu Feisty Fawn

---

### Post by bsalt on 2007-06-22
I just recently found out that the latest version of Rhythmbox supports MTP devices. I compared it to that of Amarok, and I found it to be better.

Check it out at my blog here:

[http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html](http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html)

---

### Post by DiaperJe|\|i3 on 2007-06-25
> **bsalt said:**
> I just recently found out that the latest version of Rhythmbox supports MTP devices. I compared it to that of Amarok, and I found it to be better.

Check it out at my blog here:

[http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html](http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html)

Hey Man, thanks! I'll give that a try when I get home.

---

### Post by DiaperJe|\|i3 on 2007-06-26
The latest Rhythmbox transfers media infinately better than Amarok. I can now transfer multiple albums instead of one song at a time. For some reason is absolutely balks at transfering 3 of my 40 albums. Even one song at a time. It core dumps. Very odd but much better than Amarok at this point. Pity, since Amarok is a better music player.

---

### Post by Subfusc on 2007-07-13
Minor mistake in faq: 
> sudo apt-get amarok amarok-engines amarok-xine
it's 
sudo apt-get install amarok amarok-engines amarok-xine
Might be confusing for a total noob :)

> **kfir_w said:**
> Hi,
I'm using Creative Zen Micro on Ubuntu 7.04.
MTP doesn't recognize the player:

[I]kfir@zalame:/$ mtp-detect 
No MTP devices.
No devices.[/I]

How do I get it to work??

you might wanna try 
```
lsusb
``` 
to see if it finds your device, and if it does, check if the device exist in this file:
```
sudo gedit /etc/udev/rules.d/65-libmtp.rules
```
if it does not, add it.

Btw, amarok is safe as fort nox to transfer to my iRiver Clix. And it transfers albumart to, does rythmbox have that option? ^_^

---

### Post by JawsThemeSwimming428 on 2007-07-22
subfusc,

 I am having the same issues as kfir_w with the Creative Zen Micro. I did what you said and lsusb recognized the Zen Micro and it also was listed in /etc/udev/rules.d/65-libmtp.rules. When I power the device on and plug it in Rhythmbox comes up but doesn't list any devices and Amarok doesn't see anything either. What should I do?

---

### Post by JawsThemeSwimming428 on 2007-07-23
Scratch that. I got it working with Gnomad2 and then I use Rhythmbox. Pretty easy actually.

---

### Post by treyping on 2007-08-16
all the command worked fine for me except the last one i typed in the terminal and it said

E: Invalid operation amarok


anyone know whats wrong?

---

### Post by Tom B on 2007-08-18
I have the same problem. When I plug in my Creative Zen Touch, rhythymbox pops up but doesn't list it, and amarok can't see it. It is listed when I run lsusb and it is in the file but nothing shows up when I run mtp-detect. Gnomad2 can recognize it, but I would like to use amarok if possible.

---

