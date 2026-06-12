---
title: "dvd drive doesn't play store bought, but does play my copies of them."
date: 2010-03-10
forum: Multimedia Software
---

### Post by cYb3rfOx on 2010-03-10
After many days of trying to tweak Ubuntu 9.10 desktop i386, my eyes are sore and I'm now asking for help.

This subject will focus on my dvd drive. ...Here is what I have done, but I'm not sure what I did or still need to do, or to do different. ...Thanks! 

Basically the problem is, I can't play store bought DVDs, but I can play my copies of them.

When using MDPlayer that I added to Ubuntu, I can play the copies of my store bought DVDs, but not the originals. However, when using Ubuntu 9.10's movie player, it wont do anything and I'll have to do a force quit to close it.

I learned that this may because there is a repository of packages that cannot be included into the Ubuntu distribution, as I'm sure you already knew. 
...Yet, Most people have worked around these issues.

I came across the Medibuntu site:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Running the Terminal, I added the bash command that adds Medibuntu's repositiry to Ubuntu. It also adds Medibuntu's GPG key to the keyring.
(The sudo wget - etc etc etc --quiet update)

Then I jumped down to the... "This command should be run in the Terminal, after adding the repository:" ...And did that.
(sudo sed -e 's/ etc etc etc /medibuntu.list)

So, what are your thoughts on all this?

Thanks again! 

Peace cYb3rfOx

===========================================

     HP G60-443CL laptop

    * Type: General Purpose
    * Operating System: (Now Only) Ubuntu 9.10 desktop i386
    * Processor Name: Intel Pentium Dual Core T4300
    * Processor Speed: 2.1 GHz
    * RAM: 4 GB
    * Screen Size: 15.6 inches
    * Screen Size Type: widescreen
    * Graphics Card: Intel Graphics Media Accelerator 4500MHD
    * Storage Capacity: 320 GB
    * Networking Options: 802.11n
    * Primary Optical Drive: Dual-Layer DVD+/-RW

---

### Post by PRC09 on 2010-03-10
If you scroll down the page on your link you will see the Playing encripted DVD section you have to add that as well.Use the commands for i386 or 64bit whichever system you are using. Then do the same for Playing Non-Native Media Formats,again for i386 or 64bit.That will eneble you to play the store bought DVDs......

---

### Post by cYb3rfOx on 2010-03-10
Thank you so much "PRCO9"!

You were right!

That did really put me on the right path for the solution!

I re-read the next possible Terminal options and chose the Terminal commands for:

-Playing Encrypted DVDs
-With the entire Medibuntu repository
-If you have added the entire Medibuntu repository, you just need to install the package using APT: 
-(sudo apt-get install libdvdcss2)

I'm not sure if it would have been better to choose an individual package, but the Ubuntu 9.10 Movie Player is now playing the encryped DVDs!

(You guys feel free to let me know if it would have been better for me to choose an individual package for some reason! ...Or why it was good or better to do it the way I did. ...Thanks!)

Thanks again to "PRCO9" for the help and to all the others that have been helping others! 

With my 1st cup of Ubuntu on the Forums and being helped, I now feel like part of the Linux family!  ...Thank you!

I also look forward to helping others with Linux in the future when I can.
I'll be creating some awesome Backgrounds for everyone! 

Peace and joy, -cYb3rfOx
[B]



[/B]

---

