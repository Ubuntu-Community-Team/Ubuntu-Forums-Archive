---
title: "Can we get VLC 0.8.6 on Dapper please?"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by mocha on 2007-02-01
Is there anyway for the developers to update VLC to 0.8.6a in the dapper repositories?  Thanks.  :guitar:

---

### Post by ubunter1 on 2007-02-01
vlc says to do this-  [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
im trying it now.

---

### Post by mocha on 2007-02-01
That only gets you the version already in the repositories, 0.8.4.

---

### Post by ubunter1 on 2007-02-01
on the page before the instructions it says 0.86. maybe it redirects to the older version. 
[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by mocha on 2007-02-02
I understand what you're saying but the instructions they give just use adept (as opposed to Synaptic) to install it from the standard Dapper repositories which currently only have 0.8.4 in them.

---

### Post by Perfect Storm on 2007-02-02
Compiling is a good option here. Firstly you can add/disable file formats for VLC and secondly is the optimizations which is good.


Other than that you might wait for Feisty it properly have the latest when it hit official release.

---

### Post by moogle on 2007-02-02
Hi there
tried compiling 0.8.6 from source getting all sorts of dependency errors with ./configure
such as :
configure: error: Could not find libmad on your system: you may get it from [http://www.underbit.com/products/mad/](http://www.underbit.com/products/mad/). Alternatively you can use --disable-mad to disable the mad plugin.

when I try that I get: 

checking for postproc/postprocess.h... no
configure: error: Missing header file postproc/postprocess.h.

when i get that [this]("http://wiki.videolan.org/Common_Problems#.22Missing_header_file_ffmpeg.2Favcodec.h.22_and_.22Missing_header_file_postproc.2Fpostprocess.h.22_Errors") says to > export PKG_CONFIG_PATH=location where location is the output of 'locate libavcodec.pc'

but to no avail 
still not working 
any thoughts? 
I really only want to move to 0.8.6 because I still can't play most wmv files is it perhaps that I just have 0.8.4 configured incorrectly ?

---

### Post by Moulton on 2007-02-02
When you add a special repository to 'apt' you might also have to tweak some preferences to indicate which version to select.  In Synaptic, there is a 'setting's menu item to indicate which of several available versions to prefer.

Or you can use the 'Force Version' menu item in the Package Menu of Synaptic.

I have VLC 0.8.6 installed in both x86 Ubuntu and Ubuntu on the Sparc-64.

It supports AACplus (which is why I wanted it).  But it's bewilderingly complex application to use.  It works pretty well on the x86.  On the Sparc, it often freezes up.

---

### Post by moogle on 2007-02-02
Moulton if you managed to get it working can you tell us how you did?
I've added repos to debian before by editing sources.list but what specific repos are you talking about? synaptic only lists 0.8.4 for me.

---

### Post by mocha on 2007-02-02
Yes Moulton, please share how you installed in on an x86 machine when you have time.  Thanks.

---

### Post by quagmire on 2007-02-23
I've just compiled 0.8.6a in Ubuntu Dapper and it plays flv files. The instructions are hacked mostly from [http://planet.videolan.org/]("http://planet.videolan.org/") but I think the original instructions are a bit outdated now (they were for 0.8.2) so I'll basically go through what I typed in.

- First install dependencies from ubuntu repositories, if you don't have them already

sudo apt-get install libwxgtk2.6-dev libdvbpsi3-dev libmpeg2-4-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev gcc g++ automake1.9 autoconf libtool subversion cvs libx11-dev 

- Also install libdvdcss if zone-free DVD support is desired. I've had to google a bit to find this, and I think the latest version is somewhere around 2.1.8 ? I won't go into how to install this

- I'm also going to ignore AAC support, but (outdated) instructions are there in the link

- download and install ffmpeg

cd ~
mkdir videolan
cd videolan
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg ; ./configure --enable-pp --enable-gpl ; make

- as I'm lazy, I'm also ignoring wmv9 support that is listed in the link

- now, let's install vlc player. DON'T download the 'trunk', which currently is 0.9.0, I couldn't get it to open any file. instead, we'll go for 0.8.6-bugfix

cd ~/videolan ; svn co svn://svn.videolan.org/vlc/branches/0.8.6-bugfix vlc-trunk
cd vlc-trunk
./bootstrap
./configure --with-ffmpeg-tree=../ffmpeg --enable-esd --enable-flac --enable-theora --disable-hal
make

- that should've taken a while... If you want to, you can finish off by

sudo make install


I noticed that with certain .flv files, I get a green artifact at the top of the screen and blue channel is shifted downwards a bit, if anyone knows why this is so I'd appreciate if you could tell me. Also, there seems to be a strange problem in vlc player where, once I open an flv file, I basically have to restart the program to be able to play another .flv file. bit annoying, but no biggie. as long as I get to watch family guy in linux.

---

### Post by kempfjb on 2007-02-26
hello,

I am from VideoLAN VLC media player team and a developer.
I have built vlc 0.8.6a for dapper :D

Here are the debs: [ftp://ftp.videolan.org/pub/videolan/ubuntu/pool/vlc/0.8.6a-jb/](ftp://ftp.videolan.org/pub/videolan/ubuntu/pool/vlc/0.8.6a-jb/)

I am working on making an easier way (sources.list)

---

### Post by ubunter1 on 2007-02-26
awesome! thanks for this ,ill try it now,nice to see developers involved in ubuntu and the like.=D>  i need this as im a newbie to ubuntu.do i just install all the debs?,what about the tar and the.dsc?thanks.rob.

---

### Post by kempfjb on 2007-02-26
OK. 

I am going to make an easier way tomorrow. But basically you will have to download all the .debs and dpkg -i *.deb. But wait. There is a depency problem, that I am trying to fix. :)

---

### Post by ubunter1 on 2007-02-27
thanks,ill wait for this as i dont know what id do anyways:)

---

### Post by kempfjb on 2007-02-28
allright.

add

> deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe 

to your

/etc/apt/sources.lists

run 
sudo apt-get update

sudo apt-get install vlc libvlc0 vlc-nox mozilla-plugin-vlc vlc-plugin-alsa
vlc-plugin-esd wxvlc

---

### Post by mocha on 2007-02-28
Thanks very much for this.  Since I made the original post I upgraded to Edgy.  My system upgraded without problem and now I have VLC 0.8.6.  However, the 0.8.6 installed within Edgy's repository is different from the Windows version, namely support for NSV and VP62.  Does the version in your repository support the same video formats as the Windows version?  Thanks.

---

### Post by kempfjb on 2007-02-28
Well, VLC version in edgy is not an official release... So it lacks a few things like VP62. 

You can try feisty version of VLC under edgy or wait a few days ... I'll do packages for edgy.

---

### Post by ubunter1 on 2007-02-28
> **kempfjb said:**
> allright.

add



to your

/etc/apt/sources.lists

run 
sudo apt-get update

sudo apt-get install vlc libvlc0 vlc-nox mozilla-plugin-vlc vlc-plugin-alsa
vlc-plugin-esd wxvlc

   :( this may sound stupid but do i click the link then add to my /etc/apt/sources.lists? or go to the list then just type it?.sorry absolute newb here

---

### Post by mocha on 2007-02-28
> **kempfjb said:**
> Well, VLC version in edgy is not an official release... So it lacks a few things like VP62. 

You can try feisty version of VLC under edgy or wait a few days ... I'll do packages for edgy.

Okay thanks!  I'll wait a few days.

---

### Post by Perfect Storm on 2007-03-01
> **ubunter1 said:**
> :( this may sound stupid but do i click the link then add to my /etc/apt/sources.lists? or go to the list then just type it?.sorry absolute newb here

You add it to the sourcelist, not clicking it.

---

### Post by ubu-for on 2007-05-03
> **kempfjb said:**
> Well, VLC version in edgy is not an official release... So it lacks a few things like VP62. 

You can try feisty version of VLC under edgy or wait a few days ... I'll do packages for edgy.

The Feisty version of VLC can't play VP62 videos either!

---

### Post by KrIaXPaTaLa on 2007-10-15
Worked pefectly in dapper. Thnks m8.

Regards.

KX, PT

---

