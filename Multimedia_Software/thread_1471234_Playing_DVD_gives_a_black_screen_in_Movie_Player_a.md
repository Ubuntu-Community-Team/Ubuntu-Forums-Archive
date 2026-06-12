---
title: "Playing DVD gives a black screen in Movie Player and VLC"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Confused Computer User on 2010-05-03
HI all,

As my user name suggests i'm a newb. so please be patient and understanding if I ask obvious questions.

System Specs:
RAM:          1GB
Mother board: P4P800 VM
Video:        Internal (plus a tuner card I don't use

OS:           Ubuntu 10.04 (with latest updates


Ok so a brief description. The comp initially had an ATI Radeon X1600 card I removed because it was giving more trouble than it was worth. I'll add it later if there is a chance it might make things batter. (NB the computer was painfully slow with the card installed... runs faster without it)

I installed the restricted formats pakage as per the instructions found at:
 [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

So I installed the ubuntu-restricted-extras package and then ran:

 sudo /usr/share/doc/libdvdread4/install-css.sh
 sudo apt-get install ubuntu-restricted-extras

in the terminal.

Now here is what happens. The DVD plays as I can hear it but the screen is black. moving the screen i'll get glimpses of video but not much. This happens in MOvie PLayer and in VLC. However with VLC by moving it around and going full screen I manage to get the video component working as well.

What gives? Can any one help?
Thank you.

---

### Post by dino99 on 2010-05-03
add Medibuntu repo, see below

Mirror 1:

    deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
    deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free



Mirror 2:

    deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free
    deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free



Mirror 3:

    deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
    deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

---

### Post by dnguyen1963 on 2010-05-03
I have seen the same problem.  I did not have this error with previous version of Ubuntu...must be 10.04 specific. And yes, going full screen solved the problem.  I am seriously thinking about going back to Ubuntu 8.10 (never had any problem with this version).

---

### Post by dino99 on 2010-05-03
> **dnguyen1963 said:**
> I have seen the same problem.  I did not have this error with previous version of Ubuntu...must be 10.04 specific. And yes, going full screen solved the problem.  I am seriously thinking about going back to Ubuntu 8.10 (never had any problem with this version).

remember that there is no maintenance for it

---

### Post by dnguyen1963 on 2010-05-03
> **dino99 said:**
> remember that there is no maintenance for it

Yes, but I have had 8.10 for three years and not a problem.  I have had so many issues with 10.04 already.  Quite frankly, I am sick of pushing the power button to re-boot the machine.

---

### Post by Confused Computer User on 2010-05-03
> **dino99 said:**
> add Medibuntu repo, see below

Mirror 1:

    deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
    deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free



Mirror 2:

    deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free
    deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free



Mirror 3:

    deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
    deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

Thank you for the prompt reply. Just one thing. How exactly do I do this. I googled it and found two sites that mention it. Which should I follow, and how should I modify the terminal command lines (i apologize if terminology is wrong)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://easierbuntu.blogspot.com/2008/02/adding-medibuntu-repository.html](http://easierbuntu.blogspot.com/2008/02/adding-medibuntu-repository.html)

> **dnguyen1963 said:**
> I have seen the same problem.  I did not have this error with previous version of Ubuntu...must be 10.04 specific. And yes, going full screen solved the problem.  I am seriously thinking about going back to Ubuntu 8.10 (never had any problem with this version).
I had the same experience with 10.04 (9.10 as well but not in the same way)
Ubuntu 8.04 was the first Linux distro I tried and I loved it. Mostly because it was my failsafe in case Windows refused to boot. I could use the live CD to run OO and print or transfer any files I needed for school. I hate the fact that Ubuntu is not working as well as I remember (or expect) but it is still a good alternative to Windows. (the price is sooooo right: Free)

If I can get this fixed then I'll be satisfied.

Also according to this
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)
8.04 is supported till April 2011

---

### Post by EMCGFX on 2010-05-03
Yeah, I tried using 10.04 too, went back to 9.10 my self. It has vlc or nvidia driver bugs, when watching video in VLC it cuts the video horizontally. Its funny because even in 9.10 I have same issue when using compiz effects. When I read about 10.04 features that nvidia support was improved I was excited. But after trying it, its actually supported worse.

---

### Post by Confused Computer User on 2010-05-04
Bump... any one?

---

### Post by Confused Computer User on 2010-05-04
Ok so I did as dino99 suggested using the following link as a guide.

[http://easierbuntu.blogspot.com/2008/02/adding-medibuntu-repository.html](http://easierbuntu.blogspot.com/2008/02/adding-medibuntu-repository.html)

it installed ok with no issues but my problem is still not solved. any suggestions?

Thanks.

---

### Post by dnguyen1963 on 2010-05-05
> **dino99 said:**
> add Medibuntu repo, see below

Mirror 1:

    deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
    deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free



Mirror 2:

    deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free
    deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free



Mirror 3:

    deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
    deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

Unfortunately, I still have the same problem after installing Medibuntu.

---

### Post by krfrnd on 2010-05-05
In Ubuntu 10.04 as well as the previous 9.10, I've had so many headaches trying to get "Avatar" to play in any of them (VLC/Media Player, etc.)...finally I went back to the usual 
Applications/Ubuntu software center/ and typed in _**smplayer**_...since I have a portable one on my jumpdrive for windows only & it works just super great...Yep they have one for Lucid Lynx as well (not portable).  Just install and voila!!! I am right now watching Avatar._** Disregard**_ the first prompt when you open smplayer that tells you it is outdated or not compatible.

---

### Post by dnguyen1963 on 2010-05-05
> **krfrnd said:**
> In Ubuntu 10.04 as well as the previous 9.10, I've had so many headaches trying to get "Avatar" to play in any of them (VLC/Media Player, etc.)...finally I went back to the usual 
Applications/Ubuntu software center/ and typed in _**smplayer**_...since I have a portable one on my jumpdrive for windows only & it works just super great...Yep they have one for Lucid Lynx as well (not portable).  Just install and voila!!! I am right now watching Avatar._** Disregard**_ the first prompt when you open smplayer that tells you it is outdated or not compatible.

Does smplayer work work 8.10?  I am seriously thinking about going back to 8.10 even without any future support from Canonical.  I tried both 9.04 and 9.10 already...same problems as 10.04.

---

### Post by krfrnd on 2010-05-05
*Does smplayer work work 8.10?  I am seriously  thinking about going back to 8.10 even without any future support from  Canonical.  I tried both 9.04 and 9.10 already...same problems as 10.04.*
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		 		 		 ...you know, I've been trying to install Ubuntu on this laptop since 7.10 on...no dice...all the way up to 9.04. I was elated to see it work when 9.10 came out...so I am a newbie at Ubuntu, but a voracious one, and love to learn.
But even then no matter what programs I was recommended to install to watch DVD movies, none of them worked.  Out of desperation, I noticed (in 9.10) that smplayer was there, so I installed it (like I said, I've had great experiences with the portable one (for windows) on my jumpdrive,whereas when I was at a friends place for one, none of the other applications would play certain videos, but this one would, right out of the box. It worked great!! no matter what DVD movie I played (dunno about blueray). When Ubuntu 10.04 was released, I did a complete re-install (rather than upgrade) which of course erased all 9.10.  Then for the life of me, I couldn't find smplayer in the Ubuntu software center so I went along and tried the 'others'.  Spent a sleepless night trying everything, upgrading codecs, etc, etc... from VLC to media player and anything else in between I could find on the internet. Nothing doing...finally this morning, I decided to type smplayer in the search bar (Applications/ubuntu software - far upper right corner is the search bar) rather than browse thru the programs...(which I just found out it was there all along anyway, I must have drawn a blank during the sleepless night)
Now to answer your question, I would say if you decide to go back to 8.10, go ahead and give it a shot if they provide it in the Ubuntu software department. If not try this link: [http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php)
I see your Intrepid Ibex version _**is**_ there
I think this will become one of your favorite players as well as it's ease of use. (Just stretch the screen to your liking like you would any window).  Mine is  p, li { white-space: pre-wrap; }  Version: 0.6.8 (SVN r3213)
Using Qt 4.6.2 (compiled with Qt 4.6.0)

Using MPlayer SVN r1


Sorry for being a little long-winded...I'm still new at this.

 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9243859")

---

### Post by dnguyen1963 on 2010-05-05
> **krfrnd said:**
> *Does smplayer work work 8.10?  I am seriously  thinking about going back to 8.10 even without any future support from  Canonical.  I tried both 9.04 and 9.10 already...same problems as 10.04.*
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		 		 		 ...you know, I've been trying to install Ubuntu on this laptop since 7.10 on...no dice...all the way up to 9.04. I was elated to see it work when 9.10 came out...so I am a newbie at Ubuntu, but a voracious one, and love to learn.
But even then no matter what programs I was recommended to install to watch DVD movies, none of them worked.  Out of desperation, I noticed (in 9.10) that smplayer was there, so I installed it (like I said, I've had great experiences with the portable one (for windows) on my jumpdrive,whereas when I was at a friends place for one, none of the other applications would play certain videos, but this one would, right out of the box. It worked great!! no matter what DVD movie I played (dunno about blueray). When Ubuntu 10.04 was released, I did a complete re-install (rather than upgrade) which of course erased all 9.10.  Then for the life of me, I couldn't find smplayer in the Ubuntu software center so I went along and tried the 'others'.  Spent a sleepless night trying everything, upgrading codecs, etc, etc... from VLC to media player and anything else in between I could find on the internet. Nothing doing...finally this morning, I decided to type smplayer in the search bar (Applications/ubuntu software - far upper right corner is the search bar) rather than browse thru the programs...(which I just found out it was there all along anyway, I must have drawn a blank during the sleepless night)
Now to answer your question, I would say if you decide to go back to 8.10, go ahead and give it a shot if they provide it in the Ubuntu software department. If not try this link: [http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php)
I see your Intrepid Ibex version _**is**_ there
I think this will become one of your favorite players as well as it's ease of use. (Just stretch the screen to your liking like you would any window).  Mine is  p, li { white-space: pre-wrap; }  Version: 0.6.8 (SVN r3213)
Using Qt 4.6.2 (compiled with Qt 4.6.0)

Using MPlayer SVN r1


Sorry for being a little long-winded...I'm still new at this.

 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9243859")

Thanks.  I downloaded Medibuntu repo and I can watch many movies through Totem.  I don't have Avatar so don't know if that movie would play.  I'll look for smplayer tonight and give it a try.  I'm going to wait a bit before going back to 8.10.  There are a lot of features in 10.04 that I like.:popcorn:

---

### Post by Confused Computer User on 2010-05-05
Wow... just wow... didn't expect this many replies.

Ok... So the issue still exists even after installing the afore mentioned repo.

I installed Totem but I can't find it in the list of programs. ie Applications-> Sound & Video-> Totem or whatever

I installed SMPlayer which works great so far. A Win equivalent for me would be GOM player in terms of simplicity of use. My one issue is the gamma out put. Can I increase that? My screen is kind of old so I have to play around with those setings. In vlc it's simple but with this one I have no clue.

Thank you for the ample replies but the issue still remains. Just to remind you when playing videos in VLC or MPlayer I get a black screen. I have to move the window arround in order to get to see the image. With VLC this works most of the time. With MPlayer not so much.

Thanks again.

---

### Post by n.hinton on 2010-05-05
Since upgrading from karmic to lucid, I've been experiencing the same problem as you describe with totem (my vlc is fine), odd thing though when I ran totem from a terminal (looking for clues) with ```
totem --debug
``` it behaved!

---

### Post by Confused Computer User on 2010-05-05
@ n.hinton

I ran the comand but no go. The issue still pertains.

Also why is it that I can't see Totem in my menus?

ie:Applications-> Sound & Video-> Totem

Thanks

---

### Post by III_D on 2010-05-05
I'm no power user, but here is a question even I can answer!

Its' name is not exactly correct in the pull-down menu:

When I choose Applications > Sound & Video > Movie Player, the program that opens reports itself as Totem Movie Player 2.30.0

Hope that helps!
III_D

---

### Post by Confused Computer User on 2010-05-05
> **III_D said:**
> I'm no power user, but here is a question even I can answer!

Its' name is not exactly correct in the pull-down menu:

When I choose Applications > Sound & Video > Movie Player, the program that opens reports itself as Totem Movie Player 2.30.0

Hope that helps!
III_D

	:oops: thanks III_D. That's one mater out of the way.

---

### Post by dnguyen1963 on 2010-05-06
FYI...smplayer worked well for 10.04.  There is no longer a black screen.

---

### Post by mprince on 2010-05-06
I was getting this behavior with other video types (MP4, Theora, etc) and as a workaround you might want to try this:

> Press Alt+F2 and run "gstreamer-properties"-- on the video tab, change the default output plugin to "X Window System (No Xv)."

It fixed things for me, but I haven't tried DVDs yet.

---

### Post by Confused Computer User on 2010-05-08
I tried this and it failed. In the end I went back to 9.10. I'll wait for 10.10 and hope that offers better support. But there are some others that have this issue... so if any has a solution please post.

Cheers

---

### Post by n.hinton on 2010-05-09
Latest update in lucid has fixed totem

---

### Post by tsucol11 on 2010-05-09
> **n.hinton said:**
> Latest update in lucid has fixed totem


Not in my case, movies are still not playable. I've moved on to SMPlayer which works fine.

Brian

---

### Post by mprince on 2010-05-10
> **n.hinton said:**
> Latest update in lucid has fixed totem

This update fixed the playback issue for me, too.

---

### Post by Confused Computer User on 2010-05-15
> **mprince said:**
> This update fixed the playback issue for me, too.

I can confirm this as well.
However...in my case (under 10.04... i went back..well not quite...never mind) Moving the video window around will cause the video to go black. Going Full Screen solves this so no complaints.

I'll mark this thread as solved then.:guitar:

---

