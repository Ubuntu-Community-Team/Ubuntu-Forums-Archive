---
title: "Adobe Flash Player not working on PBS Kids Sprout"
date: 2010-03-29
forum: Multimedia Software
---

### Post by ubutujim on 2010-03-29
[SIZE=3]I just started using Ubuntu and I have 2 grand kids that love PBS Kids Sprouts. The Adobe Flash Player will not work for me on this link. I have loaded the latest version 10 and I am using Firefox as a browser.  I have the Nvida chip set on my video card.[/SIZE]
[SIZE=3]
[http://www.sproutonline.com/sprout/home/](http://www.sproutonline.com/sprout/home/)



[/SIZE]

---

### Post by 2hot6ft2 on 2010-03-29
Strange, it doesn't work for me either. The games will play but the videos wont and I checked the FAQ and it says it's flash as well as right clicking on the player and it saying flash.:confused:

P.S. Welcome to the forum

---

### Post by ubutujim on 2010-03-31
I am new to Ubuntu and thought I would get more of a response to my problem?  I need help with this problem. Any help at all?

---

### Post by Chronon on 2010-03-31
Sorry.  I can't play anything from there either.  Maybe you can access some stuff through Miro instead:
[http://www.miroguide.com/search?query=Sprout&submit=Search](http://www.miroguide.com/search?query=Sprout&submit=Search)

You could always try contacting them and letting them know about the trouble you're having.
[http://www.sproutonline.com/sprout/info/contactus.aspx](http://www.sproutonline.com/sprout/info/contactus.aspx)

---

### Post by 2hot6ft2 on 2010-03-31
This may or may not help.
[http://lovinglinux.megabyet.net/?page_id=220#Flash-videos-display-only-a-symbol-and-won%27t-start-2](http://lovinglinux.megabyet.net/?page_id=220#Flash-videos-display-only-a-symbol-and-won%27t-start-2)

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
If nothing else ask lovinglinux that's his thread and website and I think that if anyone can get it going it will be him.

---

### Post by ubutujim on 2010-04-02
Hello All 
I think I know what my problem is but I do not know how to get it fixed. The problem is likely in the Adobe Flash Player. The format for the video on PBS Kids Sprout is PDK and it will not play on this Flash current version of Adobe Flash Player. If this format take off there will be a lot of web pages that will stop working. I am not sure how to get Adobe to take a look at the plug in for Firefox. If you would like to take a look at the link below and I can not make any of the videos on this page play. 



[http://theplatform.com/](http://theplatform.com/)

---

### Post by Chronon on 2010-04-02
PDK seems to stand for Player Development Kit.  > **Create faster, more distinctive players with the PDK**

thePlatform&#8217;s Player Development Kit (PDK) 4.2 has everything you need to build your own unique, Flash-based broadband video player. Completely documented and fully customizable, PDK provides an advanced player, that when paired with your content, will create a compelling viewing experience for your audience. 

It seems to be aimed at creating flash-based media players.  I don't think it's creating a competing format.  I don't know why the media players aren't working in Ubuntu.  Maybe they use a codec that isn't supported, or a feature of flash that isn't well supported in Adobe's version for Linux.

Edit: I don't know if "flash-based" should be understood to imply features that are not in flash itself or not.

---

### Post by ubutujim on 2010-04-05
Are all of the problems as hard to fix as this? I have been working for 6 day now and still no fix?

---

### Post by Chronon on 2010-04-05
I don't understand your first question.  Problems can have various causes and fixes.  You can't really generalize about them.  Adobe's flash player is proprietary software, so there's relatively little that can be done to affect its functionality.

---

### Post by ubutujim on 2010-04-05
This all started when I down loaded Ubuntu and put it on to a Dell computer. I want to use it for my grand kids. But it would not play the video on PBS Kids Sprout. I guess I should not expect it to but I did. I guess it time to just buy a copy of Windows as it will play the video I need. If I cant make Ubuntu work what else can I do? :mad:

---

### Post by Chronon on 2010-04-05
One workaround you could try: install a Windows version of Firefox with flash through Wine.  If this doesn't work then you could install Windows inside of Virtualbox and access the website from that.

However, if the computer's purpose is to play media off of that website then your best option may be installing Windows.  If you do install Windows I would remind you that you can set up the computer to dual-boot Windows and Ubuntu (as both of my machines are set up to do).

---

### Post by ubutujim on 2010-04-08
Hello All
I did get an e-mail back form the web master at PBS Kids Sprout and they ask me to install the and try all the version of the flash player. Which I have tried but none work. I still think that the software they use is part of the problem. I will just have to do as the last post suggested and load Windows back on the computer. Thank you all for your time and suggestions. :(

---

### Post by Chronon on 2010-04-08
Hi.  I just loaded up the original URL you posted in the Windows version of Firefox (installed via Wine in Ubuntu) and the videos work that way.  Maybe this is acceptable to you?

---

### Post by ubutujim on 2010-04-08
Hello All
Good new is I did get this Link working I had to install wine but that was not all I had to down load the Adobe Flash player for Firefox and load that and then it worked. Thank you all for your help :cool::popcorn:

---

### Post by Chronon on 2010-04-08
I'm glad my suggestion panned out for you.  :)

---

### Post by UserSince2003 on 2010-04-12
Try this procedure.  It worked for me:
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

---

### Post by Chronon on 2010-04-12
Thanks but both the OP and I already had Adobe's flash installed.  Are you saying that you can play videos on the mentioned site using Linux version of Adobe flash?

---

### Post by oxchronxo on 2010-04-19
Turns out it's just the flash plugin. I have it working on Edubuntu 10.04 b2.

Just to clarify, Videos & Games both work fine with this solution.

[http://chronx.info/2010/04/19/sproutonline_videos_working_on_edubuntu/](http://chronx.info/2010/04/19/sproutonline_videos_working_on_edubuntu/)

---

### Post by Chronon on 2010-04-19
Cool!  That's great news.  I wonder how that person found out about this 10.1b version.  Adobe's download page still lists 10.0.45.2

---

### Post by areteichi on 2011-05-25
I am having the same issue with [PBS Frontline]("http://www.pbs.org/wgbh/pages/frontline/view/")

I can watch the episodes that are in "News + Public Affairs Player" but not the ones that are in the Platform PDK player. I emailed PBS to asked them to post the videos using the NPA player from now on. Hopefully they will listen :)

---

