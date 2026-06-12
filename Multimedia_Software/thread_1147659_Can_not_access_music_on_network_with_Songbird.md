---
title: "Can not access music on network with Songbird"
date: 2009-05-03
forum: Multimedia Software
---

### Post by yogiman.uk on 2009-05-03
Hello

I hope someone can help me with my problem.

I am using Songbird but this seems to apply to any application I have tried.

My music is stored on the workstation in my office using Ubuntu 9.04 the music is shared as **music** from my laptop I am unable to set the SMB share as the default music folder nor browse to it.

I have read in the forums that this is because it is not mounted correctly.  However it does not state how it is supposed to be mounted.

To gain access to the drive (create the mount) I browse using Network Servers select the pc and then select the shared folder.

If this is not the correct method can someone please explain to me how I am supposed to achieve my goal.

All help welcome.

Many thanks


Yogiman!

---

### Post by rednwhitez on 2009-07-14
I am having the same problem. Did you find an answer?

---

### Post by paparozoumis on 2009-07-14
This is the **ONLY** reason I prefer to use Rhythmbox. Because it is able to read music files directly, even if they are on a network. 
With other applications, I  have to open the folder on the Network, navigate  and then choose "Open with...." 
Rhythmbox doesnt need this as it reads the specified folders automatically...

---

### Post by Grone1985 on 2010-01-05
Same problem here, if it works on rhythmbox why not on songbird?

---

### Post by yogiman_uk on 2010-01-05
That is a very good question, I must admit I am rather stumped so if anyone knows the answer to this one a helping hand would go down a treat.

I am afraid that I don't understand the choices for some of the Ubuntu default applications.  rhythmbox, fspot, totem seem somewhat unfinished in a sense.

Don't get me wrong I appreciate all the hard work the programmers put into these products, it just seems that they started but never got around to making them smooth to use!

Regards


Yogiman!

---

### Post by paparozoumis on 2010-01-07
> **Grone1985 said:**
> Same problem here, if it works on rhythmbox why not on songbird?

Here's a bump to this thread. 
I haven't found any way for players (besides Rhythmbox) to be able to see the network and then be able to play the music files from there. 
If I could make them work, I would be willing to try them out and see what their advantages are. But since my music is on my home network server and not locally on my Ubuntu machine, I have no use for these programs ....

---

### Post by yogiman.uk on 2010-01-09
I've decided to crack a nut with a hammer.  Taken off the existing audio and video software and installed XBMC which seems to handle all the video and audio in one application, yes I know it's designed more to be a media centre but put it in windowed mode and it plays everything and connects to my network shares and internet media as well.

What's the point of under kill if it doesn't do what you want.

Cheers

Yogiman!

---

### Post by Grone1985 on 2010-01-21
Hey! So I got a solution for our problem, at least for now. If you mount the share you are trying to access, it will mount it  in /.gvfs... So I made this script that you can add to your Start Apps and will mount it automatically every time you log in.

Now all you have to do is go to your home folder and look on the .gvfs folder to add the files to the library!

The script is on my last post on this thread:

[http://ubuntuforums.org/showthread.php?t=1383817]("http://ubuntuforums.org/showthread.php?t=1383817")

Cheers!

---

