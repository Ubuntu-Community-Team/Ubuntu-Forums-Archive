---
title: "Get prebuilt realtime-enabled kernel packages here"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by temcat on 2006-12-06
If you need a realtime-enabled kernel for your audio work (Jack, Ardout etc.), but don't want to compile your own kernel, get precompiled kernel package from here:

[http://archive.64studio.com/pool/main/l/linux-2.6/linux-image-2.6.18-2-multimedia-486_2.6.18-5_i386.deb](http://archive.64studio.com/pool/main/l/linux-2.6/linux-image-2.6.18-2-multimedia-486_2.6.18-5_i386.deb)

If you need to compile kernel modules, you will need the following packages:

[http://archive.64studio.com/pool/main/l/linux-2.6/linux-headers-2.6.18-2-multimedia_2.6.18-5_i386.deb](http://archive.64studio.com/pool/main/l/linux-2.6/linux-headers-2.6.18-2-multimedia_2.6.18-5_i386.deb)
[http://archive.64studio.com/pool/main/l/linux-2.6/linux-headers-2.6.18-2-multimedia-486_2.6.18-5_i386.deb](http://archive.64studio.com/pool/main/l/linux-2.6/linux-headers-2.6.18-2-multimedia-486_2.6.18-5_i386.deb)

To install the latter two packages, you will also need another package which I attach directly to the post because I don't remember where it resides in the 64studio archive.

I cannot guarantee that all your hardware will work with this kernel though. Have fun!

---

### Post by cmbryan on 2006-12-06
Great!

Can you give any specifics?  i.e. does this have the molnar patches, or is it just preemption-enabled?

Thanks

-Chris

p.s.  I can confirm that this kernel is working on edgy.

---

### Post by pljones on 2006-12-06
> **cmbryan said:**
> Great!
Can you give any specifics?  i.e. does this have the molnar patches, or is it just preemption-enabled?
Thanks
-Chris
The 64linux kernels are REALTIME (Ingo's patch) enabled, AFAIK.  I've not tried one yet...

---

### Post by temcat on 2006-12-06
> **cmbryan said:**
> Great!

Can you give any specifics?  i.e. does this have the molnar patches, or is it just preemption-enabled?



Yes, it does include Ingo Molnar patches.

BTW, just installing the kernel is not quite enough! Don't forget to tune your system as described in [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation), in the "Real-Time Support" and "Timer Resolution" sections.

---

### Post by SATTI on 2007-04-07
how can i install this into ubuntu?

I tried sudo dpkg -i packagename.deb

But it didn't work,

Thanks!

---

### Post by christhemonkey on 2007-04-07
If you are using feisty (and have universe enabled) then you can just go:
```
sudo apt-get install linux-lowlatency 
```

And reboot into your new kernel with full realtime premption.

---

### Post by SATTI on 2007-04-07
I'm not using feisty on this computer, i am using edgy. I tried feisty, but it is a little troublesome on my machine

---

### Post by christhemonkey on 2007-04-07
Ah fair enough.
If you have downloaded those .deb files, you should just be able to double click on them to install them.
(doing a sudo dpkg -i foo.deb should work as well though)

---

### Post by SATTI on 2007-04-07
I tried that; and this is what happened;

vaio@vaio:~/Desktop$ sudo dpkg -i linux-image-2.6.18-2-multimedia-486_2.6.18-5_i386.deb

dpkg-deb: `linux-image-2.6.18-2-multimedia-486_2.6.18-5_i386.deb' is not a debian format archive

dpkg: error processing linux-image-2.6.18-2-multimedia-486_2.6.18-5_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2

Errors were encountered while processing:
 linux-image-2.6.18-2-multimedia-486_2.6.18-5_i386.deb

vaio@vaio:~/Desktop$

---

### Post by christhemonkey on 2007-04-07
Sounds like an corrupt file, try redownloading it.

(though the problem might be on their end and not yours)


If redownloading doesnt work, there are several other realtime enabled kernel packages about, and personally, patching and compiling a vanilla kernel isnt so hard!

---

### Post by SATTI on 2007-04-07
you were right, i went into the ftp. i couldn't find .18, only .17 and .19.

version .19 is experimental, but i'm going to give it a whizz anyway, wish me luck!

Thanks Chris...again!

---

### Post by christhemonkey on 2007-04-07
No problem - again!!

---

### Post by SATTI on 2007-04-07
Ok, once more;)

Right the new kernel is installed, and my edgy seems pretty zippy. But, ndiswrapper wont work, of course.

So i uninstalled it, but when i try to install a version of ndiswrapper i have on cd, version 1.40,

i get errors. I think it wants me to update the build-essential or something. I tried the ndiswrapper on the edgy cd and that doesnt seem to work either

How can i now get ndiswrapper to work with this kernel. I think this might actually be the last step to my ultimate pc!!

---

### Post by SATTI on 2007-04-07
Ok, correction. I can install the ndiswrapper off of the edgy cd, but when i type 'sudo modprobe ndiswrapper' 

It says FATAL; module ndiswrapper not found.

I can type ndiswrapper, and it will bring up the usual. But i cant modprobe it???

---

### Post by christhemonkey on 2007-04-07
I believe you have to compile ndiswrapper for the kernel you are running:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#When_I_run_.27modprobe_ndiswrapper.27.2C_I_get_.27Invalid_module_format.27_or_.27Invalid_argument.27_error_or_something_similar._What_do_I_do.3F](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#When_I_run_.27modprobe_ndiswrapper.27.2C_I_get_.27Invalid_module_format.27_or_.27Invalid_argument.27_error_or_something_similar._What_do_I_do.3F)

There may be an ndiswrapper .deb package on the OP site though!

EDIT:
Ok it would seem that there is not a precompiled ndiswrapper package, you will need to obtain the ndiswrapper source and compile it yourself.
You will need the kernel headers as posted in the OP!

---

### Post by SATTI on 2007-04-07
Hmm, that sounds like a start:)

What is the OP site Chris?

---

### Post by christhemonkey on 2007-04-07
Original Posters Site, Sorry am too used to that abbreviation.

To save you looking its this:
[http://archive.64studio.com](http://archive.64studio.com)

---

### Post by SATTI on 2007-04-07
Ah I see. I had a look, it doesn't look like the developer has support for ndiswrapper. I could only find fw-cutter. Maybe that is my only option for now.

---

### Post by christhemonkey on 2007-04-07
As i said, compiling ndiswrapper is not impossible.

See here:
[http://doc.gwos.org/index.php/NdiswrapperFromSource](http://doc.gwos.org/index.php/NdiswrapperFromSource)

But use the kernel-headers from the 64studio site, and not the ones that howto tells you to install.

---

### Post by SATTI on 2007-04-07
Ok Chris i'll lookinto it. It may be tricky, because i can't just apt-get on my system because the internet isn't working on it. I suppose i could download the headers and burn them onto a cd. But then i don't know how to install them, like in the howto. I just wish i knew more about linux, i feel like i'm so close!!!

---

### Post by christhemonkey on 2007-04-07
You could download those headers to a usb stick or something, then double click on them to install them in ubuntu.

Shouldnt be too hard! :)


You are very close (it would seem!)

---

### Post by SATTI on 2007-04-07
Ok that's what I'm going to do. 

I feel a bit stupid, because i realized i can still boot up the old kernel to use the internet. I downloaded the header files, but i get this error when i launch the .deb package;

ERROR: Dependency is not satisfiable: linux-headers-2.6.19-1-multimedia

It won't let me install.

---

### Post by christhemonkey on 2007-04-08
You did remember to get both files?
[http://archive.64studio.com/64studio/64studio_1.2.0.apt/pool/main/l/linux-2.6/linux-headers-2.6.19-1-multimedia_2.6.19-1~experimental.1_i386.deb](http://archive.64studio.com/64studio/64studio_1.2.0.apt/pool/main/l/linux-2.6/linux-headers-2.6.19-1-multimedia_2.6.19-1~experimental.1_i386.deb)
[http://archive.64studio.com/64studio/64studio_1.2.0.apt/pool/main/l/linux-2.6/linux-headers-2.6.19-1-multimedia-486_2.6.19-1~experimental.1_i386.deb](http://archive.64studio.com/64studio/64studio_1.2.0.apt/pool/main/l/linux-2.6/linux-headers-2.6.19-1-multimedia-486_2.6.19-1~experimental.1_i386.deb)

And then install the larger one first.

---

