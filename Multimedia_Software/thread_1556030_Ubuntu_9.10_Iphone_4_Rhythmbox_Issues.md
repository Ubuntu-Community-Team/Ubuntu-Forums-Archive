---
title: "Ubuntu 9.10 Iphone 4 Rhythmbox Issues"
date: 2010-08-18
forum: Multimedia Software
---

### Post by Wolfbird79 on 2010-08-18
im using iphone 4 with ios 4.01 ..
Rhythmbox sees phone no issue ..
when i drag song to iphone it appears to copy to iphone no issue(it shows like it copied to iphone).. 
when i unplug phone from usb and look at music library the song is not there.. when i plug usb back in song on iphone doesnt show in rhythm box..

---

### Post by Wolfbird79 on 2010-08-20
Using ifile on my iphone 4 i can see the songs in the F folders in side the music dir and they will play... However the ipod app still will not see the music.  Please help.

---

### Post by astralbat on 2010-08-21
I'm getting exactly the same issue. Strangely the phone doesn't show up in gtkpod, nor Banshee so those aren't options.

---

### Post by Wolfbird79 on 2010-08-23
I can get the phone to show up in gtkpod but, it has the same issue in from there.

---

### Post by jonasbdotcom on 2010-08-24
any news about this? I have the same problem.

---

### Post by jillybeans13 on 2010-08-24
Can someone please post on here as soon as these issues with the latest version of Ubuntu and iphone4 are fixed.

I really need some music on my phone and don't want to give itunes the satisfaction of wiping my phone again. I was so excited to have the new iphone4 until I realised that nothing is compatible with it yet. Well nothing that isn't Apple!!! booo.

If anyone knows of any working way to transfer music to the iphone 4 without itunes and Windows please help xxx. Thanks in advance. :KS:D:D:D:KS

---

### Post by astralbat on 2010-08-26
Ok, libimobiledevice is the library package that makes this is all work by magic. It seems however from what I can gather that it's libgpod that does the music syncing part and according to [www.libimobiledevice.org](www.libimobiledevice.org) it's not exactly working just yet for the iPhone 4 but they should be making a new release soon so stay patient!

---

### Post by zosky on 2010-09-15
libimobiledevice 1.0.1 / gtkPOD 0.99.14 / libGpod 0.7.93 / iphone4 iOS 4.0.2

can mount successfully with ifuse. can read db in gtkpod, but the last track in list shows 'garbage' in genre field. ( i loaded a few tracks with iTunes )

i tried adding a new track ... file copied to *[iphone-mount]/iTunes_Control/Music/F37/libgpod309569.mp3*... saved db ... iphone shows sync screen ... gtkPOD reports error "unsupported checksum type"... and the new track is not in iPod.app :( 

i'm guessing this is because gtkpod pod doensn't yet have an iphone4 setting @ properties>model ? i love the iphone, but i hate how apple doesn't want us doing this & changes things with every device & iOS just to lock us out again!

i hope this gets sorted soon

UPDATE: this is as far as anyone can get ATM. both gtkPod & Rhythmbox use the libGpod library for managing the music db (source:[gtkpod.org/wiki/Libgpod]("http://www.gtkpod.org/wiki/Libgpod"))...
> Latest stable release is version 0.7.2, and latest development release is 0.7.94. The stable release supports iPods up to the iPod Classic and the iPod Nano 4g. The development release has support for all iPod models, as well as for non-jailbroken iOS devices (iPod Touch, iPhone). **iPad and iPhone/iPod Touch 4 are only _supported as read-only devices_**. Support for the iPod Shuffle and iPod Nano released on September 2010 is at this point unknown, please get in touch with us if you have such a device up for testing. 

---

### Post by ada-m on 2010-09-18
Unfortunately I have no solution to this issue but I did have any interesting case of this issue. 

I used to have an iPhone 3G and everything worked great under 10.04 rhythmbox with no issue. When I upgraded to 4.0, all of the music wiped -no big deal as I was expecting that- but when I added it all back on there I had the same issue as you all, the music wasn't showing up on the device. Rebooting the phone, nothing could seem to get it to work.  I actually put ~10gb of music on there and it really seemed to slow down the phone, for example I would click on my text message button and would have to wait about 10-15 for it to load.  Terrible.  Now the strange thing is after about a week or two the music randomly appeared on the phone, but was still running extremely slow.  Fortunately I didn't have to keep it that long as I jail broke and sold it on eBay when I got the iPhone 4. The jailbreak and restore to default did fix the lag issues.

Needless to say I haven't tried to sync the phone with Ubuntu yet and do not plan on it until I am hearing people have success. 

Just thought I'd share,
Adam

---

### Post by TwizzyDizzy on 2011-03-09
Hi dudes,

now here's a solution to those of you who have a jailbroken iPhone4
This solution is independant of your libimobiledevice-version.

My Setup:
iPhone 4, 16GB, firmware 4.2.1
Jailbroken with greenpois0n RC5 (although RC6 is already available)

How-To:

- Install the openssh-server Package via cydia
- Install the AVPlayer Package via cydia
( do the following steps only if you installed the openssh-server for the first time and if you did not already change your password
- login to your iphone via ssh as user "root" with password "alpine"
- change the password, for it's the default password via "passwd" command
- login to your iphone via ssh as user "mobile" with password "alpine"
- change the password, for it's the default password via "passwd" command
)

Now open AVPlayer from Springboard and Choose "config" in the upper left. Enter the filetypes you want to use, seperated by a space. In my case this is only "mp3"
Now you can upload your MP3-Files via SFTP (SSH-FTP) to /private/var/mobile (or any folder you did create in that place) and listen to them via AVPlayer.

For me it's like the best solution for I organize my MP3s myself and I didn't like the iPod app to much all the while.

Have fun!

---

### Post by muskie25 on 2011-08-15
It seems that "Unsupported Checksum Type" affects every aspect of the "Save Changes" command.  I originally used Banshee to manage my iPod, but discovered that the Touch 4g isn't supported.  The Banshee sync did nothing but scramble my album art.  Next I downloaded gtkpod, which also doesn't support the iPod Touch 4th Generation.  I manually reset all my album art (3 hours), then saved changes.  Oops... unsupported checksum type.  Changes not saved.  :(   I'm using the newest version of gtkpod (using libgpod 0.7.93).  Apple changed the codes on the new touches, I know that, but hasn't anyone figured out a way around it yet?  They did with all the other touches and Ipods.  

If it helps, I'm using 

-Linux Mint 11 Katya, 32 bit
-iPod Touch 4th Gen, OS. 4.1 (or whatever it came with, I never updated or jailbroke)
-gtkpod
-Toshiba laptop

Another note, the iPod is not displaying any error messages.  It appears to sync.  

Ahh well, if anyone has a solution, that would be greatly appreciated.  Now I need to give Apple a call and ask them why they changed the codes in the new touch... :) Or jailbreak.  

Thanks, muskie.

---

