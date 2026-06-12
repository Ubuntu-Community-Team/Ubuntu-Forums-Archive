---
title: "[SOLVED] Xbox360 Media Center Extender"
date: 2008-08-11
forum: Multimedia Software
---

### Post by TDragon on 2008-08-11
I have been trying to find a linux-equivalent for the Media Center Extender service offered by Vista & XP. I have recently switched back to Linux, and want to retain as much functionality as possible when playing files through the 360.

I was going to install TwonkyVision, but from what I read in their forums, it would not work through MCE on the 360.


I was also considering Fuppes, but haven't been able to get an answer for that program as well.



Can anyone offer some advice/tips for 360 streaming?

---

### Post by calito on 2008-08-11
I have heard that fuppes is a very good program for media sharing to the xbox but whenever I try to install it I always get problems. Check out their website. [http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

---

### Post by TDragon on 2008-08-11
Yeah.. same problem here when I try to install it.

---

### Post by calito on 2008-08-11
Twonky works for me as a media server for my xbox but I don't know what you mean by it doesnt work through MCE. Twonky shares audio picture and video files

---

### Post by TDragon on 2008-08-12
> **calito said:**
> Twonky works for me as a media server for my xbox but I don't know what you mean by it doesnt work through MCE. Twonky shares audio picture and video files
 
The Media Center Extender feature allows the 360 (or another approved device) to pair with a PC in your network that has Media Center installed (XP Media Center Edition or Vista Home Premium/Ultimate). You will be presented with an interface that appears very similar to what you would see on the PC (when using MC).
 
From what I have read on the Twonky forums, the progam will not work through the media center link on the 360 (or when you press the media center button on the remote). Instead, I read that you have to go through a more complicated route under the media file browser of the 360 (the section where you would view content saved to the 360's HD or if you had a Zune or iPod).
 
 
If that's not the case. By all means, I'll install it. If I can get the install script to work properly that is.

---

### Post by ilrudie on 2008-08-12
I use ushare.  You have to run it with the -x flag to force xbox360 compatibility mode.  I just modified the rc script so it starts in compatibility mode.  It's been working great.

---

### Post by Person_1873 on 2009-06-11
so what was the solution, ushare only allows file sharing via the file browser on the xbox, was there any way to use the 360's media center extender functionality with a graphical interface on a linux machine? other than having a VM running vista?

---

### Post by hgri89 on 2010-06-01
Just to clear Up, this is an issue that I have been looking for as well. The Xbox 360 has a feature which makes it act like a thin client to any of the Windows media center enabled Operating systems (XP MCE 2005, Vista Home premium or Ultimate and Windows 7 Home premium, Ultimate and Enterprise) When the Xbox 360 pairs up with one of those computers The Media center interface application is streamed tho the XBOX 360. All of the proccessing is done by the Main computer. Like like a thin client. An advantage to this is the ability to be able to watch tv, play media and use any application on the XBOX 360 that is media center compatible. The only things I have found are not processed by the main computer is the decoding of the media, everything else aka the main interface is processed by the main computer, but i presume to save bandwidth Microsoft decided to let the 360 decode the media to save bandwidth.

To pair the XBOX360 with Windows media center fist you need to go to the xbox360 and enter the media center application, it will say that it has not been set up, and will ask you if you want to set it up, when you select next it comes upw with an 8 digit code in the form of XXXX-XXXX which is when you go to the main computer, open media center and click add extender it will ask for the code which the xbox has provided once this code is entered it goes about searching for the XBOX 360 (I presume this is done over UPNP for whenever an xbox 360 is connected to a network with any of the windows versions mentioned above they always ask if you want to start the pairing process automatically). Once media center has found the XBOX the xbox goes into the loading screen while media center changes the sharing permissions on all of the media on your computer to allow the XBOX 360 to access them.

A few other things that may help.
The connection to the media center is never instant, It can take a few seconds to find the media server (a searching screen comes up) and then it can (depending on the main computers speed and network speed) take at least 30 seconds to 2 min to connect before the interface comes up. I know that that time is not spent waiting for the media center service to start for it is always running.

I know that if this service can be accessed the CPU power of the XBOX 360 *_**might** _*become accessible to the user.

I know that there is a lot of authentication going on between the XBOX 360 and the media server and I believe that the code that was entered earlyer on may have something to do with the authentication/ecryption, for this changes every time the XBOX 360 is re-paired with a media center computer.

So all in all. I have been wanting to be able to use the XBOX 360 to stream media from my TV cards to the XBOX 360 for A, the 360 is very easy to use, it is an all in one Media game package, and B I don't have my 360's plugged into a TV i have them plugged into computer screens and C I am able to schedule recordings from my XBOX 360 without the requirement of direct access to the main computer. I play a lot of XBOX 360 games on-line and watch a lot of media. This is the only reason I'm willing to cause my self pain by using Win 7 Ultimate as a server. Its starting to get to the stage where i will just install UBUNTU on it then install windows 7 inside a virtual machine to get media center extending capabilities (my TV cards are USB that god) The big thing is that by doing this the Power saving capabilities of my gigabyte motherboard go out the window for the virtual machine wont like it going into power save mode. (I have a gigabyte motherboard and the power saving features are excelent (as show here the savings [http://www.tweaktown.com/articles/1348/gigabyte_des_and_asus_epu_tested/index4.html](http://www.tweaktown.com/articles/1348/gigabyte_des_and_asus_epu_tested/index4.html) )

---

### Post by Kuci on 2012-06-30
ushare just works great and this way is better, than use XBOX as extender.

---

### Post by overdrank on 2012-06-30
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

