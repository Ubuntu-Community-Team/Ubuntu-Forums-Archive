---
title: "Enconding Vorbis with better quality: aoTuV beta5 patch"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by pjssilva on 2007-12-28
Ayoumi aoTuV beta 5 patch is considered the [best vorbis tuning in Hydrogen Audio forums](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis), a very well regarded audio discussion group. 

Following the suggestion in a link from Yota [post](http://www.hydrogenaudio.org/forums/index.php?showtopic=49555&pid=520752&mode=threaded&show=&st=75&#entry520752), I have patched Ubuntu 7.10 (gutsy) source for vorbis with aoTuV beta 5.

To make the life of Ubuntu users easy I am making my packages available in my PPA. To use it just add

deb [http://ppa.launchpad.net/pjssilva/ubuntu](http://ppa.launchpad.net/pjssilva/ubuntu) gutsy main

to the /etc/apt/sources.list file. If you want the source, add

deb-src [http://ppa.launchpad.net/pjssilva/ubuntu](http://ppa.launchpad.net/pjssilva/ubuntu) gutsy main

After that you may do a "apt-get update; apt-get upgrade" or just wait for the automatic update manager to kick in. After the update, any audio encoded using vorbis will benefit from the tunings. It doesn't matter if you use the command line encoder (oggenc) or something that  depends on the vorbis libraries (like sound-juicer the default music extractor in Ubuntu). 

Feel free to use it and, please, let me know if you find any problem.

By the way, Ubuntu libvorbis file is based on libvorbis 1.2.0, while the aoTuV patch was created againt 1.1.2. Hence, the original patch did not apply cleanly to the source (some line offsets and a trivial failure). It required some simple manual intervention.  I have tested my changes comparing the average bit-rate of my package and the static binary from [ hydrogen audio  wiki](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis) and they are basically equal (as much as one can expect from floating point implementations).

---

### Post by pay on 2007-12-30
Could you send me your modified patch? I was trying to figure out how to compile libvorbis 1.2.0 with aotuv but couldn't get it to work...

---

### Post by Yoochan on 2008-01-01
Youhouuuuuu

thank you pal !!!

I really have to learn how to use launchpad... seems funny

I couldn't patch 7.10 with the same tricks I used for the previous patch... glad you succeded

(I'm Yota on hydorgenaudio :))

---

### Post by pjssilva on 2008-01-02
> **pay said:**
> Could you send me your modified patch? I was trying to figure out how to compile libvorbis 1.2.0 with aotuv but couldn't get it to work...

I don't really have the patch now. You can get it by downloading the original source from Ubuntu (use apt-get source libvorbis)  and then downloading mine source (add the deb-src line in my post and the do a "apt-get update" followed by a "apt-get source libvorbis"). You can then create the patch yourself.

---

### Post by pjssilva on 2008-01-02
> **pjssilva said:**
> I don't really have the patch now. You can get it by downloading the original source from Ubuntu (use apt-get source libvorbis)  and then downloading mine source (add the deb-src line in my post and the do a "apt-get update" followed by a "apt-get source libvorbis"). You can then create the patch yourself.

I have done the work myself (I realized that it was a good idea to keep the patch). Here is the patch.

Of course this patch is governed by Aoyumi's license which is says:

> 
aoTuV Beta 5

aoTuV" tunes up Xiph.Org's libvorbis uniquely. 
A license is taken as "BSD-style license" as well as original libvorbis.


---

### Post by pjssilva on 2008-01-02
> **Yoochan said:**
> Youhouuuuuu

thank you pal !!!

I really have to learn how to use launchpad... seems funny

I couldn't patch 7.10 with the same tricks I used for the previous patch... glad you succeded

(I'm Yota on hydorgenaudio :))

Yota,

You are the responsible to make me work on this patch! It took me some time (I had to wait for the holidays to find free time), but here it is. Enjoy. :-)

---

### Post by o.besner on 2008-01-13
It worked for me, even without the patch. I've been working on getting aotuv to work for hours. The repository trick worked like a charm.

It's way too hard for nothing. Xiph should incorporate Aotuv in their official release...

---

### Post by disturbed1 on 2008-01-13
aoTuV's patches were merged into official oggvorbis code some time ago. Post beta 4 only adds enhancements for low bit rate encoding (sub 96kbs) Not much of an improvement for those of us that use Ogg for their music library at say -q 4 and above.

If you're into icecasting low bitrates, or mono encoding aoTuV is a good choice, otherwise, it doesn't add anything but inflated file size at higher q levels.

---

### Post by Major_Kong on 2008-01-14
pjssilva, could you make a package that would not substitute the installed libvorbis ? 
I already found this in rarewares.org* , but i can't seem to compile it from source.

*
[http://xmixahlx.dyndns.org/debian/source/oggenc-aotuv_1.0.1+aotuv-5.dsc](http://xmixahlx.dyndns.org/debian/source/oggenc-aotuv_1.0.1+aotuv-5.dsc)
[http://xmixahlx.dyndns.org/debian/source/oggenc-aotuv_1.0.1+aotuv-5.tar.gz](http://xmixahlx.dyndns.org/debian/source/oggenc-aotuv_1.0.1+aotuv-5.tar.gz)

I find this solution overall better than replacing the installed official vorbis versions with the aoTuV patched versions.

---

### Post by Major_Kong on 2008-01-20
Got it compiled (ubuntu 7.10 64bit):

[http://rapidshare.com/files/85217758/oggenc-aotuv_1.0.1_aotuv-5_amd64.deb.html](http://rapidshare.com/files/85217758/oggenc-aotuv_1.0.1_aotuv-5_amd64.deb.html)

It's a standalone CLI encoder, so there's no need to replace anything.

---

### Post by pjssilva on 2008-01-24
> **Major_Kong said:**
> Got it compiled (ubuntu 7.10 64bit):

[http://rapidshare.com/files/85217758/oggenc-aotuv_1.0.1_aotuv-5_amd64.deb.html](http://rapidshare.com/files/85217758/oggenc-aotuv_1.0.1_aotuv-5_amd64.deb.html)

It's a standalone CLI encoder, so there's no need to replace anything.

I don't see the reason not to replace the original files. Having a separate static binary only forces you to remember to call the right CLI encoder every time. You can configure some ripping tools to use the new encoder, like grip, but other may he harder to configure, like the standard gnome ripper (sound-juicer). Mine solution is transparent to the user.

The only changes made in the source code are on the encoding library, if you want to encode with aoTuV beta 5 this is the most transparent way. No other portion of the vorbis library is touched.

---

### Post by sojyujai on 2008-01-29
Nice.  Thanks pjssilva. 
I tried to figure this out some time ago but it was over my head.
Setting up the repository was a nice touch!

---

### Post by logos34 on 2008-03-07
> **pjssilva said:**
> I don't see the reason not to replace the original files. Having a separate static binary only forces you to remember to call the right CLI encoder every time. You can configure some ripping tools to use the new encoder, like grip, but other may he harder to configure, like the standard gnome ripper (sound-juicer). Mine solution is transparent to the user.

The only changes made in the source code are on the encoding library, if you want to encode with aoTuV beta 5 this is the most transparent way. No other portion of the vorbis library is touched.

Great thread! Wish I'd checked for it before I went ahead and installed aotuv beta5.

I used the instructions over at the [Hydrogenaudio ogg page]("http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis") to install both the static linux binary (-->Static GCC 4 compile) and to [compile it from source]("http://wiki.hydrogenaudio.org/index.php?title=Compiling_aoTuV")  (with the 'prefix=/usr/local'  so as not to disturb my default libvorbis 1.2 libraries).  

I'm confused, though.  It says to 

> Call oggenc as 
LD_PRELOAD=`echo /usr/local/lib/libvorbis*.so` oggenc -q4 foo.wav 
 
Works great from the CLI--and a lot faster, too, since it's optimized to run on my 64-bit ubuntu. But it's a hassle to do it that way.

But how do you call it with Grip, for instance?  What **command-line executable **do you use?

I'd really like the option of using EAC with the oggenc2.84 (lancer), Grip or ABCDE  with the aoTuV beta5, and anything else with the default Xiph libvorbis 1.2.

---

