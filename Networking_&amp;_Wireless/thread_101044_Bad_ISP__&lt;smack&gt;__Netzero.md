---
title: "Bad ISP  &lt;smack&gt;  Netzero"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by djheadley on 2005-12-08
I know, I have a bad ISP but it's all I can afford right now.  I'm using Breezy and until yesterday I had everything working, then I re-installed because I didn't have a swap partition and decided that it would be easier to re-install.  Unfortunately I lost my notes on how to get Netzero working.  I have an external modem, installed jre from Sun, checked everything I can think of.  I installed the Netzero software from the Linspire site (the one that worked before) and added a line to the bash script file to link ttS3 to /dev/modem.  I still can't get it to work!  What am I forgetting?

djheadley

---

### Post by djheadley on 2005-12-09
No Ideas?  Anyone?

---

### Post by djheadley on 2005-12-11
I know Netzero sucks and I am looking in to alternatives but I can't do anything until after Jan 1 (holidays and all).  I had it working once but lost my notes.  Any isea where to start?

djheadley

---

### Post by mips on 2005-12-11
What is netzero ?
What hardware are you using ?
Who is the ISP ?
Post links where possible.

---

### Post by Bartender on 2005-12-11
Hi, mips -
Hope you don't mind if I interject...
Netzero is a low-cost ISP here in the States.  Juno & Netzero combined a few years ago.  I'm still running Juno on my M$ machine.  I got the Ubuntu CD's in the mail last night so anxious to install to a spare machine in the next coupla days and start finding out what's gonna work and how much my remaining brain cells can handle. 
Not sure about Netzero, but Juno (the older Juno 5 that I'm using anyway - I think Juno 6 just uses Outlook Express?) has proprietary software to dial and to get e-mail.  That makes it a real headache within Linux, although I've seen a few reports of people making it work (in a fashion) with Wine and/or a program called rasspy.  Netzero's main page:

[http://www.netzero.net/](http://www.netzero.net/)

I'm watching this thread 'cause if dj gets help (or figures it out on his own) I may be able to apply to my situation.  I notice that the Netzero website claims to be compatible with Linspire.  dj mentions that he got the Linspire code from Linspire's site.  I don't understand how he did that.  I visited their site and it looked to me like you had to log in in some way that verified you owned a copy of Linspire before they'd give you access to the Downloads page.  If there's a way around that, and the Linspire code could be jury-rigged to run non-Linspire versions of Linux, I might be able to put it all together and get Juno on Ubuntu.  
I e-mailed Juno the other day, and someone wrote back saying they don't support Linux.  He didn't mention Linspire at all.

---

### Post by mips on 2005-12-11
[QUOTE=Bartender]Hi, mips -
Hope you don't mind if I interject...
[/QUOTE]

Not at all ;) 

Will follow this up tomorrow, gonna catch some ZZZZzzzzzzz now. Maybe someone else will respond in the mean time.

---

### Post by mips on 2005-12-12
I pm'ed both of you.

---

### Post by mips on 2005-12-12
For Juno look here, [http://ubuntuforums.org/showthread.php?t=17428](http://ubuntuforums.org/showthread.php?t=17428)

I have also read comments on the net about people getting it to work without the Juno software. Somehow they mention putting the modem into *dumb* mode and putting the entire username [email]xxxx@juno.com[/email] + password in and it works.

---

### Post by mips on 2005-12-12
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=348691](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=348691)
[http://ubuntuforums.org/showthread.php?t=90497&highlight=netzero](http://ubuntuforums.org/showthread.php?t=90497&highlight=netzero)
[http://ubuntuforums.org/showthread.php?t=22178&highlight=netzero](http://ubuntuforums.org/showthread.php?t=22178&highlight=netzero)   This looks promising
[http://ubuntuforums.org/showthread.php?t=70438&highlight=netzero](http://ubuntuforums.org/showthread.php?t=70438&highlight=netzero)   One of DJs previous posts

---

### Post by mips on 2005-12-12
You might be able to get the .deb files to work. Else you might have to recompile from source.

The ideal option id to get rid of the software altogether.

---

### Post by djheadley on 2005-12-13
I did get it to work, after a fashion, but now I can't download my e-mail with Thunderbird or log on to Yahoo Messenger with GAIM.  Also, this new version of NetZero software puts a navigation bar on the screen!!!!  I thought when I upgraded from the free version that I got rid of that!!!!

Anyway, I guess I'll try to work these problems out before I write a how to.  Meanwhile I guess I'll have to leave W&%)@# on my computer.  Yech!!!  Thanks for all the help and I'll let you all know how it goes.

---

### Post by Bartender on 2005-12-13
Hi, dj -
Looking forward to your "How-to".  I followed the various links on the first page of this post and whoah it's over my head.  But I don't have my Ubuntu test machine running yet so don't know what's truly beyond my grasp until I try...
Can I ask you something?  On your M$ machine, when you use Netzero's program, does it have its own proprietary e-mail software or does it use Outlook Express?

---

### Post by djheadley on 2005-12-13
I dual boot and use Thunderbird on both sides.  I think I'm going to have to uninstall the new netzero.deb and try again with an older version.  Everything works OK on the Windows side. :mad:

---

### Post by mips on 2005-12-13
Gents, this might be a good incentive to switch ISPs. I have read other recommend other ISPs with direct dial (no funny software) for the same price as Juno/Netzero.

---

### Post by djheadley on 2005-12-19
I got it going again but I'm still having some problems.

1) I have to run the netzero bash script from a root terminal.  Is there a way to be able to run this from the applications menu?

2) I have to go to a root terminal to run Gaim.  Again, is there a way to be able to run this from the applications menu?

After I get these 2 problems solved, I'll write that HowTo.   :???: 

djheadley

---

### Post by poptones on 2005-12-19
I tried both netzero and netscape. I wasted a month screwing with both of them. Netzero never worked, netscape sorta worked but I was unable to get into any secure sites. Netscape's support in particular was really, really bad in that it required several (very unpleasant) calls to their support lines to get them to stop billing me for a service that never worked properly.

I now pay the regular $20 a month for dialup from a local provider, and I'll never screw with these cut-rate unpleasantries again.

---

### Post by djheadley on 2005-12-19
I agree with you but when you can only afford the cut-rates, you have to put up with a certain amount of aggrivation.  I am looking in to alternatives but I have to stay at what I pay for Netzero and I also have to have a nationwide service as a couple of my relatives aren't on the internet and I want to be able to get my messages if I go to see them.

---

### Post by mips on 2005-12-20
[QUOTE=djheadley]I got it going again but I'm still having some problems.

1) I have to run the netzero bash script from a root terminal.  Is there a way to be able to run this from the applications menu?

2) I have to go to a root terminal to run Gaim.  Again, is there a way to be able to run this from the applications menu?

After I get these 2 problems solved, I'll write that HowTo.   :???: 

djheadley[/QUOTE]


There should be a way to do #1. Will look into it.
For #2 you should not require root to run Gaim. What happens when you try and run it without root ?

---

### Post by djheadley on 2005-12-20
[QUOTE=mips]There should be a way to do #1. Will look into it.
For #2 you should not require root to run Gaim. What happens when you try and run it without root ?[/QUOTE]
If I try with just gaim, it starts up with no accounts and after I set up an account (yahoo) the program tells me that I've been disconnected.  When I start with sudo (in the app menu) then it doesn't start.  I have to go to a root terminal in order to get it to run.

---

### Post by djheadley on 2005-12-25
I'm still having the same problems, but I'm getting used to them.  If I don't get any more suggestions, I'll write the howto as is with a call for solutions.  Thanks all for your help.


djheadley

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-26
Have you tried running their client in vmware? It would not work for me as I connect via a linux router, but if you're running it all on one machine it seems like a good shot.

---

### Post by djheadley on 2005-12-26
The netzero software is working (I used it to connect today) but I still have these 2 problems:

1) I have to run the netzero bash script from a root terminal. Is there a way to be able to run this from the applications menu?

2) I have to go to a root terminal to run Gaim. Again, is there a way to be able to run this from the applications menu?

I'm not so much concerned about me but I'd like to write a howto for others and I want to make it as easy as possible.  Not everyone is as stubborn as I am.

:lol: 

djheadley

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-26
> Is there a way to be able to run this from the applications menu?

The netzero software is written for linspire, a distro where every user is "root," so I doubt it... unless you want to run linspire.

---

### Post by TimelessRogue on 2005-12-26
Hey, folks, let's not go making things more complicated than they need to be.  I use both Juno and Netzero with Breezy 5.10 and Firefox and have never had a problem.  And it doesn't involve using outside software.  I'm currently on a DSL and/or wireless connection but was dial-up before that and used the same method.  It even worked just fine back in Windoze.

Obviously, you need to have a hot connection to the internet.

Then I simply enter [http://webmaila.netzero.net](http://webmaila.netzero.net)  or [http://webmaila.juno.net/](http://webmaila.juno.net/)

This gets me to the login screen and from there it's a piece of cake.  Works for me ... should work for you ... give it a shot ... no software involved ...

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-26
> Obviously, you need to have a hot connection to the internet.

And when your only "hot connection to the internet" IS netzero....?

You are confusing mail access with internet access. It ain't the same horse.

---

### Post by TimelessRogue on 2005-12-26
Exactly ... that's what a "hot connection" is ... a modem set-up/dial-up number or DSL connection is just what I meant.  BUT ... the real point is there's NO Netzero or Juno software involved ... just a "hot connection" and Firefox.  So don't start smacking your ISP around ... they're there waiting for you ...

You can log in to the Netzero home site ([http://my.netzero.net](http://my.netzero.net))  OR to the "mailroom" ... either one will allow you to log in to Netzero with your username/password ... so, no, I'm not confused ... and again, there's no ISP software involved at that point.  You DO need to know the local number for them though ...

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-26
OK, I don't know what you're thinking but I don't think there's much getting communicated here. Having a dialup number for netzero is NOT a "hot connection." It's not a "hot connection" until you are allowed access to their wan, and to get that access you have to use their software. You cannot just call a dialup number and enter some magic address in your web browser to get "hot." If you could no ISP could stay in business because few would ever pay them for service.

---

