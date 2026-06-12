---
title: "Why this insanity with libfaad0/2??"
date: 2007-11-25
forum: Multimedia Production
---

### Post by GMaq on 2007-11-25
Hello,

    I have been using Linux for about a year now and after flipping through several distros (MEPIS,Feisty,Mint,openSUSE, and now Gutsy) I am getting extremely frustrated that I can't get these 4 applications to install together in their latest versions, Cinelerra, Debian-Multimedia's stable ffmpeg, AviDemux, and WinFF (The best Linux ffmpeg GUI bar none!) 

    I prefer the ffmpeg from Debian Multimedia because it has all the libraries I need and the Medibuntu one doesn't. No dts or ac3 support,?! C'Mon!

    The cause of this irritating problem is libfaad0 or libfaad2 will not get along. For instance ffmpeg wants libfaad0 so won't install without annihilating libfaad2, Cinelerra and vice versa. Avidemux also whines about this conflict and won't install. Both of these libfaad libraries are doing the same job (decoding aac) so why is there two of them?

     I have encountered this issue in both Feisty 32bit and now Gutsy 32bit, i can't believe there are not more posts on this topic. For any serious multimedia enthusiast these are core programs to be using! 

     I have tried an ffmpeg SVN install and encountered the same issue. I have also tried substituting Kdenlive for Cinelerra and the latest version 0.5 is completely useless due to well documented A/V sync issues when clips are dragged onto the timeline. I can use the Windows version of WinFF under Wine, but the Windows ffmpeg DOS window will not appear to monitor the progress of the encode.

    I have been dual booting with XP since I first became interested in Linux. I have learned a lot over the last year and can do 90% of my former Windows tasks using Linux, this multimedia issue is the only thing really holding me back from formatting that XP partition.

   I am hugely impressed with Ubuntu in general, and have had to abandon other distros due to a lack of recent multimedia packages.  
Forgive my frustrated "tone" this is a very small library that has been giving me a huge headache for many months!

    Any guidance would be greatly appreciated, even if it means compiling ffmpeg from a different source. I can live without AviDemux, but Cinelerra and a full ffmpeg are imperative!

    Thanks for reading!:)

---

### Post by eye208 on 2007-11-26
Put libfaad0 into a separate folder and run applications that require it like this:

LD_LIBRARY_PATH=<path to libfaad0 folder> ffmpeg ...

See "man ld.so" for more info.

---

### Post by GMaq on 2007-11-26
eye208,
      
     Thanks very much for replying, I will look into that. If I am successful I will post back to let others know. Thanks Again

---

### Post by GMaq on 2007-11-26
OK,
        Checked out the whole ld.so thing, Waaay over my tiny head. To begin with, even installing the libraries from source would require one version to uninstall the other in order to complete would it not?

        Any other options?

---

### Post by eye208 on 2007-11-27
> **GMaq said:**
> even installing the libraries from source would require one version to uninstall the other
There is no need to compile, install or replace anything in your system. You can download the binary versions of ffmpeg and libfaad0 from debian-multimedia.org, extract the .deb files into your $HOME folder somewhere and run the ffmpeg executable from there. That's the whole point of LD_LIBRARY_PATH. Any conflicting versions of libfaad in your system will be ignored because the paths specified in LD_LIBRARY_PATH will be searched first.

---

### Post by GMaq on 2007-11-27
eye208,

     Thanks for your continued help, I wasn't aware that binaries could be run from a folder in this fashion, I learned my "something new" for today.:)

---

