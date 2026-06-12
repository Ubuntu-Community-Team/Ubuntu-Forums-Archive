---
title: "Finally got my Blu-ray working on Gutsy"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by pwn on 2008-02-19
I tried compiling the kernel with the UDF 2.5 filesystem patch and messed it up (No experience with all that). But I found a precompiled one from this forum (thanks to **ac4000**) and it was easier than I thought.

Here's a link to download it: [http://stuff.gautham.net/index.php?path=software%2F&download=udf.ko.tar.gz](http://stuff.gautham.net/index.php?path=software%2F&download=udf.ko.tar.gz)

The original udf.ko is located in /lib/modules/2.6.22-14-generic/kernel/fs/udf 

So make a backup of it before you try this, and copy the new one there and reboot. Thats it! You should now be able to mount your Blu-ray or HD-DVD discs. (I use Gutsy 32-bit, but you might wanna try it anyway if you're using another version. If it doesn't work, just replace it from the backup you made)

As far as playing movies go, it's a real pain. I used DumpHD to dump the files to the hard disk. You'll need aacskeys and libaacs to decrypt the keys. I couldn't get that to work. When you put in the path to your disc's mountpoint in DumpHD, you'll get the DiscID (see screenshot). Just use that and do a search on the doom9.org forums. Maybe someone may have posted their key already there. (I found the key for mine in a less than a minute :D) If you've found it, just add that in your KEYDB.cfg found in the DumpHD folder and run it again (type sh DumpHD.sh). It'll execute DumpHD.jar which is java based so you'll need to install java.

Another good site is decrypthd.org which has **MKB Viewer**, an app to check your Disc's MKB version. Versions upto 3 can be decrypted. If it's version 4 (New movies are) then you're out of luck. I have one movie that's V3 and one that's V4. I guess next time I'll check beforehand if the keys are already available so that I can be sure of it working on Linux.

If you have an HD-DVD drive, you can probably decrypt it on the fly and stream it to Mplayer so that you don't have to have 40GB of free space, but it isn't possible for Blu-ray it seems.

The dumped movie should be playable on mplayer but please posts the results here about how it went. I'm getting audio but no video so it's probably just a codec I'm missing, and I'm looking into it.

As far my hardware is concerned, I already do have an HDCP compliant display and video card so playing it on Windows is not an issue, but thats what I want to avoid; Rebooting, just to watch a movie :(

DumpHD screenshot:
[img]http://images.gautham.net/uploads/0cc55cfbd47bfc4a654f2881858bbdb7.png[/img]

---

### Post by addisor on 2008-02-19
Do you know where I can find a 64bit udf 2.5 patch?

---

### Post by snakeeyes on 2008-02-19
do u really have to compile your own kernel, I am using opensuse and I have the kernel source, can't I just apply it to that?

---

### Post by pwn on 2008-02-19
I'm not sure. Like I said, Not knowing exactly what to do, I took help from someone who didn't know either, tried compiling the kernel and failed. Just try replacing your udf.ko and see if it works. If it doesn't then copy the old one back. 

I don't know about 64-bit, but you could try this and see what happens.

---

### Post by snakeeyes on 2008-02-19
> **pwn said:**
> I'm not sure. Like I said, Not knowing exactly what to do, I took help from someone who didn't know either, tried compiling the kernel and failed. Just try replacing your udf.ko and see if it works. If it doesn't then copy the old one back. 

I don't know about 64-bit, but you could try this and see what happens.
I know of a link to the udf patch but do u know of the link for kernel 2.6.22, all I could find was kernel 2.6.24.

---

### Post by pwn on 2008-02-19
Not for a precompiled one but here you'll find it for different kernels.

[http://sourceforge.net/tracker/?group_id=295&atid=300295](http://sourceforge.net/tracker/?group_id=295&atid=300295)

---

### Post by snakeeyes on 2008-02-19
> **pwn said:**
> Not for a precompiled one but here you'll find it for different kernels.

[http://sourceforge.net/tracker/?group_id=295&atid=300295](http://sourceforge.net/tracker/?group_id=295&atid=300295)
Thanks, I am using kernel 2.6.22.

So all I need to do is:

cd /usr/src/linux-2.6.22.17-0.1  (I am using openSUSE on this machine)
bzcat <path_to_patch_file> | patch -p1

Then I just reboot and blu ray should work right? No compiling and stuff neccessary?

---

### Post by snakeeyes on 2008-02-19
come on, anyone?

---

### Post by glug101 on 2008-02-19
> **snakeeyes said:**
> come on, anyone?

If it is a patch for the kernel, you will need to compile.  It's actually not as bad as it sounds.  It used to be considered the ultimate config for your system, but now it's much simpler.  

Here is a link to the walk through for Ubuntu.  I can only recommend that you DO NOT use the plain vanilla kernel on kernel.org for this.  The Ubuntu kernel comes pre-patched for you with all the normal Ubuntu goodness that you are used to.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) edit: actually, I can't recommend this howto.  It seems to complex than it needs to be, and misses setting up the bootloader, that I feel should be part of a proper compiling kernel howto

Hope this helps!

---

### Post by snakeeyes on 2008-02-19
> **glug101 said:**
> If it is a patch for the kernel, you will need to compile.  It's actually not as bad as it sounds.  It used to be considered the ultimate config for your system, but now it's much simpler.  

Here is a link to the walk through for Ubuntu.  I can only recommend that you DO NOT use the plain vanilla kernel on kernel.org for this.  The Ubuntu kernel comes pre-patched for you with all the normal Ubuntu goodness that you are used to.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Hope this helps!
Hi, thanks for the link but really I don't want to risk breaking my system with a custom kernel right now, do u know when the Linux kernel will have udf 2.5 by default?

---

### Post by glug101 on 2008-02-19
> **snakeeyes said:**
> Hi, thanks for the link but really I don't want to risk breaking my system with a custom kernel right now, do u know when the Linux kernel will have udf 2.5 by default?
Hmm, good question.  If it is stable, I would guesse that it would be the next stable release of the kernel (2.6.x, whatever the next one would be).  And I just read a bit of the guide and it does not cover grub like I thought it would :(  

As long as you name the kernel something different and leave your original kernel bootable in grub, there should be no danger.  I'm currently trying out some risky settings for my Athlon kernel (the stock Ubuntu kernel just didn't work right), but I left the original kernel as is.  When my new kernel doesn't work (and you will almost always botch your first kernel ;) ) I just boot with the stock one to see what it broken.  

If I have time, I'll look up some docs on grub and post here.  Or better yet, find a good forum post for it.

Cheers!

---

### Post by glug101 on 2008-02-19
> **snakeeyes said:**
> Hi, thanks for the link but really I don't want to risk breaking my system with a custom kernel right now, do u know when the Linux kernel will have udf 2.5 by default?
Oh, and the patch might be available by default in the plain vanilla kernel awhile before it makes it to the compiled kernels available in the Ubuntu repositories.  I would guesse that it might not be available in the repositories till Hardy. (Although I could easily be wrong.)

---

### Post by snakeeyes on 2008-02-19
I hope it becomes available by default, anyone have any news about this? Does linux kernel 2.6.24 have it?

---

### Post by glug101 on 2008-02-19
After further review, I cannot recommend following the instructions on the link I posted earlier.  They are useful, but not good for a beginner (which it states at the beginning) I am very sorry about wasting space on the forums like that.  I'll attempt to post better instructions later and put a link to them here.

---

### Post by pwn on 2008-02-19
I don't know if it'll be available on Hardy. I haven't downloaded the beta version. But this patch has been available for a while and I was looking forward to seeing it included with Gutsy but it wasn't. I had asked several times but nobody seemed to know either.

Everytime I went to the IRC channel asking about UDF 2.5, they'd shut me off either by saying "Blu-ray doesn't work on Linux", or pointing me to that link about Blu-ray and HD-DVD on Ubuntu (Fiesty) which doesn't have any instructions on patching.

Recently I messed up my ext3 partition when I resized it, and I currently have a temporary ubuntu installation before i format again and install it from scratch, so I thought what the hell, I'll give it a shot even if it's likely that I'll mess it up, and I did when I tried patching myself.

If you're a beginner like me, it makes sense to have another installation in VMware so you can patch the kernel within that and then just use the udf.ko file from it so that you're not taking any chances with your actual Ubuntu installation, and that's exactly what I'll do next time I need to do this sort of thing.

Note: I think this patch is for read-only. I haven't tried writing to blanks so I'm not sure.

---

### Post by snakeeyes on 2008-02-19
I heard Nero Linux 3 supports burning and reading, is this true?

---

### Post by pwn on 2008-02-19
Yes but you'll still need a patch that'll let you write, I think. I'll buy a few blanks next month or so, and test it :)

---

### Post by snakeeyes on 2008-02-19
> **pwn said:**
> Yes but you'll still need a patch that'll let you write, I think. I'll buy a few blanks next month or so, and test it :)
Good Luck and if u find out anyway we can include bluray support without compiling please tell me, and also whether distros like suse and ubuntu will put it in by default.

Thanks!

---

### Post by pwn on 2008-02-19
Dumped Blu-ray movie, played in Mplayer (The one in the repositories does not play it properly). You can use the rc2 version available at [www.getdeb.net](www.getdeb.net)


Click for Large version
[[img]http://www.screenshots.cc/view_thumb/3d0061832/Screenshot-MPlayer.png[/img]](http://www.screenshots.cc/view_image/3d0061832/Screenshot-MPlayer.png)

---

### Post by snakeeyes on 2008-02-19
> **pwn said:**
> Dumped Blu-ray movie, played in Mplayer (The one in the repositories does not play it properly). You can use the rc2 version available at [www.getdeb.net](www.getdeb.net)


Click for Large version
[[img]http://www.screenshots.cc/view_thumb/3d0061832/Screenshot-MPlayer.png[/img]](http://www.screenshots.cc/view_image/3d0061832/Screenshot-MPlayer.png)
Thanks, I will see that, is mplayer RC2 stable?

---

### Post by pwn on 2008-02-20
Yes it is. Played without any problems.

---

### Post by snakeeyes on 2008-02-20
it can play bluray movies that means with drm?

---

### Post by pwn on 2008-02-20
No, that's what DumpHD is for, to decrypt the movies and copy to your hard drive.

---

### Post by snakeeyes on 2008-02-20
> **pwn said:**
> No, that's what DumpHD is for, to decrypt the movies and copy to your hard drive.
Do u think I should wait till Linux has support by default, it should be anytime now right, now that bluray has won the war?

---

### Post by pwn on 2008-02-20
I don't know. The format war should have nothing to do with it. Both Blu-ray and HD-DVD use the UDF 2.5 filesystem. They should have already enabled it in Gutsy but looks like they might not until it becomes more mainstream. Hardy will be released very soon so you can wait if you want.

---

### Post by snakeeyes on 2008-02-20
I think opensuse is implementing it as well, opensuse is my favorite distro thats why I can't ait for them to put it in. What about Mandriva, I heard their paid version has all sorts of proprietary codecs, will it include bluray?

---

### Post by pwn on 2008-02-20
How would I know?

---

### Post by snakeeyes on 2008-02-21
> **pwn said:**
> How would I know?
just asking, aren't there any Mandriva users here?

---

### Post by fredthefrenchy on 2008-02-25
I have a question : How can you watch the movie when it's a bluRay dump. That is the comand line with Mplayer to watch it ?


Another question, I did not find the Key for the movie The Patriot. Someone have ?


> 
DumpHD 0.4 by KenD00

Opening Key Data File... OK
Initializing AACS... OK
Loading aacskeys library... OK
aacskeys wrapper 0.2 by KenD00

Initializing source... 
Source is a directory: using disc mode
Disc type found: BluRay BDMV
Searching /cdrom/BDMV for files...
/cdrom/BDMV/index.bdmv
/cdrom/BDMV/MovieObject.bdmv
Searching /cdrom/BDMV/PLAYLIST for files...
/cdrom/BDMV/PLAYLIST/00000.mpls
...
Searching /cdrom/BDMV/BACKUP/BDJO for files...
Searching /cdrom/CERTIFICATE for files...
Searching /cdrom/CERTIFICATE/BACKUP for files...
Source initialized
Identifying disc... OK
DiscID : 20B9E25037FBD69AAFB82B8E6BD1DB26A5C7D364
Searching disc in key database...
Disc not found in key database
Retrieving keys from source... 
Executing aacskeys: ./aacskeys "/dev/scd0" "/media/.bluray" v
aacskeys v0.2.6

Error opening Media Key File /dev/scd0/AACS/MKBROM.AACS

Could not retrieve the Volume Unique Key.
Either accskeys has not started at all or it failed.
See log for details.
Failed retrieving keys from source


There is no AACS/MKBROM.AACS on the bluray disk. may be it's only for HD-DVD.


I have UDF2.5 and I can mount the BD disk.
I have also decryptHD and HDDVDFS
(Sorry for my english , I'm french !)

---

### Post by addisor on 2008-03-02
Can't help you with your problem yet, but where and how did you get UDF2.5 to work? really keen, I have 64bit kernel.

---

### Post by HellSpawn on 2008-04-07
Hello, I'm trying to get the KEY for 2 movies, one is The Simpsons Movie and all that I get is:

```

sudo bin/linux/aacskeys /cdrom v

aacskeys v0.2.9

Current path:                 /home/user/aacskeys_0.2.9



```

I left it there the whole night and still no more output. :confused:

I'm running Ubuntu 8.04 beta kernel 2.6.24-15-generic 64bit, I compile UDF 2.5 module and aacskeys exec and lib too, 4GB Ram, QuadCore Q6600 2.44Ghz, JDK 1.5.

Any clues??:confused::confused:

---

### Post by caramelsoul on 2008-05-06
OK, so im getting confused. Can i play blu-ray movies if they are straight from my hard drive. For example, if they were ripped on another machine and i just transfered the ripped file to my Ubuntu machine, would i be able to play it with the right hardware?

---

### Post by 3rdalbum on 2008-05-21
> **caramelsoul said:**
> OK, so im getting confused. Can i play blu-ray movies if they are straight from my hard drive. For example, if they were ripped on another machine and i just transfered the ripped file to my Ubuntu machine, would i be able to play it with the right hardware?

Yes, but you don't need extra hardware to play them if they have been ripped and decrypted.

---

### Post by alffjeld on 2008-05-22
hi mates!
have anyone tried to applyed the udf 2.5 patch on heron? or is it already there? i have looked after info on that, but not found anything. i have downloaded the patch, but there are not any info on the homepage of the project on how to use it.

---

### Post by alffjeld on 2008-05-22
i forgot to ask, does anyone maybe have the working udf.ko for the 2.6.24-17 generic kernel to share? im on a 64bit system if that has anything to say?

---

### Post by tamoneya on 2008-05-30
ive gotten 64 bit hardy to work with udf 2.5.  I followed these steps:
[http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)

---

