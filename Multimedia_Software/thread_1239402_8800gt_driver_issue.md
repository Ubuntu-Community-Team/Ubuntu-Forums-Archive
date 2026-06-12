---
title: "8800gt driver issue"
date: 2009-08-13
forum: Multimedia Software
---

### Post by Demijinx on 2009-08-13
Hi, im brand spankin new to the forums, and I know this has been asked before, but all the threads are very old and i was hoping that perhaps there had been some headway made on the problem.

I recently installed ubuntu onto my EVGA sli/e6600 setup, and im running two 8800gts. When i try to install the drivers that are suggested by ubuntu, the system hangs on reboot leaving me with "checking battery status" as the last thing to read. Myself being complely useless in ubuntu the only way back into operating system for me is a fresh install. Ive read that there are beta drivers that support the 8800s that have to be "manually installed" but i dont know how to do that. 

I love Ubuntu so far and if i could just clear this up i would be in hog heaven, but as it stands now the fans are running at a rediculously high speed and my videos are laggy to the point that they are unwatchable.

Help please! Thanks.

---

### Post by coldReactive on 2009-08-13
Try this:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by Demijinx on 2009-08-14
> **coldReactive said:**
> Try this:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)


Thanks for the response! Im not entirely sure im running 32bit linux, but i think i am. I downloaded the [http://www.nvidia.com/object/linux_display_ia32_185.18.31.html](http://www.nvidia.com/object/linux_display_ia32_185.18.31.html) drivers for the 8000 series for 32bit linux and installed them like the thread said. Everything installed fine but i still got the "checking battery status" deal when i restarted. Is there a different driver set i should be using?

---

### Post by Demijinx on 2009-08-14
Bump. Help please? I really dont want to go back to windows with my tail between my legs....

---

### Post by dagrump on 2009-08-15
Well, to find out if you are running 32 or 64, you would enter uname -m in a terminal.
So then we can determine if you have the wrong drivers, but I would guess they would not install & you would get a wrong architecture error.

---

### Post by Demijinx on 2009-08-15
> **dagrump said:**
> Well, to find out if you are running 32 or 64, you would enter uname -m in a terminal.
So then we can determine if you have the wrong drivers, but I would guess they would not install & you would get a wrong architecture error.


Alrighty that command returns
i686

does that tell us what we need to know?

---

### Post by coldReactive on 2009-08-15
> **Demijinx said:**
> Alrighty that command returns
i686

does that tell us what we need to know?

That means you have a 32-bit machine.

---

### Post by Demijinx on 2009-08-15
> **coldReactive said:**
> That means you have a 32-bit machine.

Well that confirms that i have been using the right drivers then! When I install the newest drivers manually i get the same results as when I let ubuntu do it, the hanging at boot. When i followed this thread [http://ubuntuforums.org/showthread.php?t=623180](http://ubuntuforums.org/showthread.php?t=623180), and grab the 169. drivers i get this. I have no idea what this means. Thanks for all the help guys.

[IMG]http://i280.photobucket.com/albums/kk194/Rygaiden/img_0170.jpg[/IMG]
[IMG]http://i280.photobucket.com/albums/kk194/Rygaiden/img_0171.jpg[/IMG]
[IMG]http://i280.photobucket.com/albums/kk194/Rygaiden/img_0172.jpg[/IMG]
[IMG]http://i280.photobucket.com/albums/kk194/Rygaiden/img_0173.jpg[/IMG]

---

### Post by Demijinx on 2009-08-17
Bump! Desperate for help!

---

### Post by Isaacgallegos on 2009-08-17
Sorry, it's very challenging to get a response on this forum. 

The only thing I can tell you is I'm running a 8800GTS and a 7300 GT. The 8800 GTS runs great when you want to work with a single monitor. But if you try to run 3 or 4 monitors (which would require the use of the second card) you can't get past the point where Ubuntu tries to run the video drivers (right after it checks the battery status). 

Get into Ubuntu using just one card and use the **System>Administration>Hardware Drivers** application to install the correct dirivers. Reboot. Then try to edit xorg.conf to use both video cards and all of your monitors. This is the point where I can't go further.

---

### Post by Demijinx on 2009-08-17
> **Isaacgallegos said:**
> Sorry, it's very challenging to get a response on this forum. 

The only thing I can tell you is I'm running a 8800GTS and a 7300 GT. The 8800 GTS runs great when you want to work with a single monitor. But if you try to run 3 or 4 monitors (which would require the use of the second card) you can't get past the point where Ubuntu tries to run the video drivers (right after it checks the battery status). 

Get into Ubuntu using just one card and use the **System>Administration>Hardware Drivers** application to install the correct dirivers. Reboot. Then try to edit xorg.conf to use both video cards and all of your monitors. This is the point where I can't go further.

Holy hell! I didnt even give any thought to the SLI setup causing issues. Yeah, im only using a single monitor. Eocf.com gave me some tips to try as well. If i can getting running without having to remove a card to do it that would make me happy because i do plan to dual boot this system at some point so I can still play games. I will hit up some other drivers and report back.


SUCCESS! Well... sorta. I got the 190 installed and it gave me the hang again so I pulled one of my 88s out and everything worked! So im guessing the drivers dont support SLI. Kinda shoots my dual boot gaming dreams in the foot if i cant get it working. Thanks a lot for all the help guys. Now that i have really gotten to play with it I can definitely say it was worth the trouble.

I will try to install the other card tonight and will update.

---

### Post by Demijinx on 2009-08-19
Okay its official. Yoy guys all suck to a degree that cant be expressed. This is the most badass OS ever devised and you didnt tell me about it. I feel like ive been pissing away my geekhood not having this. LOL. Holy hell. EVERYTHING works! First time! WHY isnt the world using this?! Thanks so much guys!!!!

---

### Post by dagrump on 2009-08-19
Well now, did you get it figured out or not? I can't tell whether you are being sarcastic or complaining.
I will still attempt to help getting SLI running, if you didn't get it ironed out. I have 2 machines running in SLI w/o issue, so the drivers do support it.
It's your call.

---

### Post by Demijinx on 2009-08-21
> **dagrump said:**
> Well now, did you get it figured out or not? I can't tell whether you are being sarcastic or complaining.
I will still attempt to help getting SLI running, if you didn't get it ironed out. I have 2 machines running in SLI w/o issue, so the drivers do support it.
It's your call.

Lol i wasnt bitching. I really love it. Ive been pretty busy with work lately so i havent messed with SLI. Though i did get an error on the last restart. Something about Nvidia and the kernel. It only runs in low graphics mode now so im going to try reinstalling the drivers.

---

### Post by dagrump on 2009-08-21
I keep cutting & pasting this same old how-to, maybe it will help. Yeah it's kinda disjointed. 

Okay, I think this will fix you up. With both cards installed & bridged (does your mobo require a card flipped or jumper switched?) I'm assuming & you know how dangerous that is, that if you reboot you get a terminal type login. then try the following.
After the drivers are installed & it boots back up, go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.
This is what my xorg.conf looks like, yours will be different due to detected hardware.

---

### Post by Demijinx on 2009-08-24
Im not on to tackling SLI yet, something with the new updates is clearly not compatible with the drivers im using. Everything works fine until i update. Im going to try updating and then installing the drivers and see if that does anything for me.

---

