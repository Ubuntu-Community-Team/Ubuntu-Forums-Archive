---
title: "blank DVD not recognized"
date: 2009-07-20
forum: Multimedia Software
---

### Post by camppen2 on 2009-07-20
I am running Ubuntu 8.10 (Intrepid Ibex). When a blank cd is inserted it is mounted and a helpful dialog comes up asking what I would like to do with it. When a blank dvd is inserted it is not recognized. When I try to burn a dvd in Brasaro or Gnomebaker it keeps saying to insert a blank disc even though one is already in. 
Restarting with dvd inserted does not work. I have googled and can't find any help. A lot of people seem to have the problem but no solution.
Is there a setting that I have missed? I have a feeling it is something simple and I am being dense.
Thank you for any help you can give.

---

### Post by wojox on 2009-07-20
You do have a DVD Writer installed on your computer right?

---

### Post by camppen2 on 2009-07-20
Actually that is a good thought. It is a different computer and I am so used to having a writer I didn't check that.
If it doesn't I am going to feel so STUPID!
I am at work now so I will have to wait till tonight to check it.

---

### Post by ghostborg on 2009-07-20
I did have problems with the DVD drive with 8.10 until I checked Proposed updates in the software sources. Hmmm, why not upgrade to Jaunty?. Try K3b for burning, if that doesn't work then you do have some serious problems.
I use Nerolinux3 ($20) for a compatibility issue with Multisession UDF discs between Ubuntu and Windows. Thats my 2 cents.
Good Luck to you.

---

### Post by camppen2 on 2009-07-20
Thanks ghostborg, I'll give K3b a try and check out Nerolinux3. I'm not against buying products, I use Moneydance and love it. I was kind of waiting for some of the bugs in Jaunty to be worked out first.

---

### Post by wojox on 2009-07-20
I actually just upgraded this morning to Jaunty I was thinking the same thing about bugs and glitchs but all is well so far.

---

### Post by camppen2 on 2009-07-21
Yes, it is a writer. I have the same problem on another computer running Intrepid too.

---

### Post by grantjohnston on 2009-07-22
I've had this same problem here [http://ubuntuforums.org/showthread.php?t=1137929](http://ubuntuforums.org/showthread.php?t=1137929) and can't figure out what the HELL to do. Like I said there. I've been doing end-arounds just because I can't burn on this damned thing. I've wound up filling my laptop up with stuff because I can't burn on this damned thing.


If ANYONE has any ideas. I will personally come to your house and make a hand party.


I guess it's a bit different, it doesn't find anything at all.. It just spins up, or says nothing at all. Very irritating....

---

### Post by camppen2 on 2009-07-22
The light on my drive blinks rapidly then goes dark. Nothing happens and if I try a burning app (Brasero or Gnomebaker) it just keeps saying to put a DVD in. It recognizes cd-r discs and dvd movies, a dialog box asks what you would like to do. This also occurs on my other computer with different specs but running Intrepid.The drive works fine in windows so it isn't the drive. I don't think it will help to upgrade to Jaunty as I have heard it has trouble too. I have seen a lot of people complain about the problem but no one seems to be able to fix it.
I can burn in windows but I am trying to get away from it.
Other than this problem Ubuntu is great! Played with bluetooth last night and it was much easier to do than in windows. Put the usb adapter in and up pops the bluetooth icon! Cool!

---

### Post by grantjohnston on 2009-07-22
> **camppen2 said:**
> The light on my drive blinks rapidly then goes dark. Nothing happens and if I try a burning app (Brasero or Gnomebaker) it just keeps saying to put a DVD in. It recognizes cd-r discs and dvd movies, a dialog box asks what you would like to do. This also occurs on my other computer with different specs but running Intrepid.The drive works fine in windows so it isn't the drive. I don't think it will help to upgrade to Jaunty as I have heard it has trouble too. I have seen a lot of people complain about the problem but no one seems to be able to fix it.
I can burn in windows but I am trying to get away from it.
Other than this problem Ubuntu is great! Played with bluetooth last night and it was much easier to do than in windows. Put the usb adapter in and up pops the bluetooth icon! Cool!


I have an idea...


What burner are you using? That COULD be the problem, maybe we're all using the same burners...? or they have similar components and that's throwing off *nix.


Mine's just an HP LightScribe 740b.


What are you guys using?

---

### Post by martinbaselier on 2009-07-22
Just a thought. The DVD burner needs to have the DVD description in it's firmware to be able to recognize it. 

[http://en.wikipedia.org/wiki/Book_type](http://en.wikipedia.org/wiki/Book_type)

There is also some data at the beginning, describing the maximum writing speed. I remembered this problem occurring in the past when doing support on windows machine. I wouldn't know the impact on the linux way of handling things though. I hardly use any cds or dvds anymore.

---

### Post by camppen2 on 2009-07-23
I have a Dell Dimension E310 using the writer that cam with it. I don't think that is the problem though. It happens on my other computer, home built with a Lite-on writer.

---

### Post by grantjohnston on 2009-09-04
Is there STILL no resolution to this?

---

### Post by sprilutsky on 2009-09-05
Here is how I went around this problem and found a workaround.

1. Open up a Brasero window/session, but leave it alone for a sec.
2. Open up a File Browser as a second Window/session
3. Drag and drop .avi file(s) from File Browser window into the Brasero Window
4. Click on "Burn" - you should not only see the correct DVD media, but also be able to burn avi format.

Let me know if it worked.

Thanks

---

### Post by camppen2 on 2009-09-07
I have decided that the problem is in the writer itself and Ubuntu. It doesn't seem to like some of the Dell writers. I have Ubuntu Ibex installed on two comps, one Dell and one home built. On the home built box Ubuntu sees the blank disc just fine. On the Dell it will not. I'm going to try changing out the writer on the Dell for a generic one and see if that works. They are cheap now and I can always use a spare writer is it doesn't work.

---

### Post by grantjohnston on 2009-09-07
That's not a bad idea. I would stay away from HP DVD dual-layer lightscribe drives.

That's what I'm running and I haven't had any luck on Jaunty, yet. 

Also. You're running intrepid.... Hmm a lot of us are having the problem with jaunty. Have you tried using jaunty, or only intrepid?

Also. I haven't had a chance to try and do the above mentioned method on burning, but I will try it and get back to you. 


Grant

---

### Post by camppen2 on 2009-09-07
My mistake, I'm running Jaunty,forgot that I upgraded. But I did have the problem on Ibex, that's why I upgraded.
I plan on just getting a cheap drive. I always had good luck with Lite-on. I'm not worried about it too much because I do have one drive that works. Just bugs me that the other one won't.

---

### Post by grantjohnston on 2009-11-01
> **camppen2 said:**
> My mistake, I'm running Jaunty,forgot that I upgraded. But I did have the problem on Ibex, that's why I upgraded.
I plan on just getting a cheap drive. I always had good luck with Lite-on. I'm not worried about it too much because I do have one drive that works. Just bugs me that the other one won't.

Let us know if you have you upgraded to Karmic and are still having the issues.

Thanks


Grant

---

### Post by grantjohnston on 2009-11-01
[SIZE=7]IT'S THE DRIVES!!!!!![/SIZE]



Guys, it's the f*cking drives!


Even after updating the firmware for the HPDVD740b(i) in a Doze environment, it still wouldn't work.

I had an extra DVD+/-DL laying around from a computer I had worked on that I pulled out. I threw it in, put it on cable select and put in a DVD and it popped right up! Even the disks that wouldn't work on this machine before worked great!


I started uncontrollably screaming when I found out it worked.


So, for all of you that have drives that aren't working, post them up in this thread and hopefully someone else that has that same drive can swap it out and try a different one to see if it can be added to the 'blacklist' of non-working drives.

I'll start it off.




[size=4]**HP740B(i)**[/size] 



Good luck everyone!



grant

---

### Post by camppen2 on 2009-11-02
I agree, it is the drive. I upgraded to 9.10 and now it will recognize a blank cd in Brasero but not a DVD. Still will not recognize either if just inserted (should give option box "you have just inserted a blank cd/dvd....").
My computer is a Dell Dimension E310, OEM CD/DVD writer part #D9934. Everything else works great including Compiz.

---

### Post by grantjohnston on 2009-11-02
> **camppen2 said:**
> I agree, it is the drive. I upgraded to 9.10 and now it will recognize a blank cd in Brasero but not a DVD. Still will not recognize either if just inserted (should give option box "you have just inserted a blank cd/dvd....").
My computer is a Dell Dimension E310, OEM CD/DVD writer part #D9934. Everything else works great including Compiz.

Hmm, that's odd, I couldn't get even blank CDs to work.

Do you have a spare one laying around? Or even if not that, you could just run to BB or something and snag one on sale and try it out. If it doesn't work, then just return it :D. 

Or you could switch the face plates and return it anyway :lol:


As for the popping up, do you have gnome-volume-manager installed?


Acutally, come to mind, I have had your problem happen before. 

Does the light on the DVD burner keep blinking when the disc is in there, like it's trying to read it? Also, what media are you using? I had this same issue 2-3 distros ago, and it was my media. My burner HATED Sony DVDs and it stayed that way until the drive didn't recognize any blank media at all. If you have any extra DVD media laying around you might try a different brand of DVD. TDK and pretty much every other brand did the trick for me. 


Let me know what you find out

Good Luck, 

Grant


EDIT: Here's my thread for that problem. Do tell me what you found out. [http://ubuntuforums.org/showthread.php?t=636530](http://ubuntuforums.org/showthread.php?t=636530)

---

### Post by camppen2 on 2009-11-03
I had the problem before too- a different writer solved the problem. The problem just interests/irritates me as to why it does it. I guess Ubuntu just doesn't like some writers, especially Dell.
Yes the light on the writer keeps blinking for a while, like it's thinking, then stops. I have tried a variety of brands of media, none of them worked.
I didn't install the volume manager but it should be installed by default I think. I'll have to check when I get home (at work now).
I ran into a couple of problems with 9.10 so I'll look for manager as I try to fix it.

---

### Post by ken487 on 2009-11-13
I just had the same problem on two different thinkpads, a T60 and T500.  Blank CDs are recognized, but DVDs aren't.  The DVDs are recognized in <yuck>windows</yuck>

---

### Post by huanix on 2009-11-15
I spent 15 minutes troubleshooting the same problem. I was using a SATA Lite-On DVD/CD RW Litescribe drive - model iHAS422 and it was not recognized at all by 2.6.31-14-generic; not in nautilus or by lshw. When i swapped in an old PATA drive things worked out just fine. 

Interestingly, I was also having a recurring kernel panic on boot that may be explained by this. I have a dump, but i haven't looked at it closely enough to comment.. i'll follow up later.

---

