---
title: "Ipod can't be seen Banshee"
date: 2008-04-25
forum: Multimedia Software
---

### Post by fhmanas on 2008-04-25
I have an old 4th Gen Ipod, i think, anyway, I installed Banshee for synaptic and it does not recognize the IPOD.  IPod is recognized by Gutsy and Rhythmbox, but I want to try out Banshee.

Also, once Banshee recognizes the Ipod, how do stop Rhythmbox from opening whenever I attach the IPOD?

---

### Post by fhmanas on 2008-04-25
Ok, figured it out, apparently the 2 problems were interrelated.  Banshee was not seeing my IPod because Rhythmbox was using it first.  So to solve it, I fixed it so that IPod will run Banshee instead of Rhythmbox,

For those with similar noobie problems, the method is just to replace rhythmbox with banshee in System -> Preferences -> Removable Drives and Media -> Multimedia Tab -> Portable Music Players

Then that's it, whenever you attach your ipod it will run banshee and be detected by banshee

---

### Post by fhmanas on 2008-04-27
In Hardy Heron, portable media was removed for the Removable Drives and Media, there is a similar option in Preferred Applications, don't know if this is the same but I know that this did not help detect my ipod in banshee.

---

### Post by fhmanas on 2008-04-29
Update:

After trying Preferred Applications again, and choosing Custom and manually typing 'banshee', my IPod can be seen again by banshee.  Somehow choosing Banshee from the dropdown list does not work.


Update:

Lost it again. It ran once, so at least I know that it was not banshee.  Somehow Heron is messing it up and goes back to Rhythmbox.  If only I know where to locate the actual configuration file it is messing with.

---

### Post by ansky on 2008-04-30
I also had problems with Banshee recognizing my ipod after upgrading to Hardy.   Based on a comment in this bug report [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/139226](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/139226) I installed podsleuth and now it seems to be working.

---

### Post by fhmanas on 2008-05-01
thanks for pointing me to the right direction, i don't know if podsleuth had anything to do with it but the trick that worked was making all the users a member of haldaemon

---

### Post by Ernesto RD on 2009-08-05
Tried all the methods above, non worked. My ipod was just insivible to banshee

But i found the solution...

**Just Remove Rhythmbox!** :)
go to synaptics pacacke manager, and mark rhythmbox to _completely_ uninstall, uninstall it, and thats it.
now banshee can see my ipod just fine.

hope this helps

---

### Post by LuisGMarine on 2009-12-29
thanks installing podsleuth helped out a lot.

---

### Post by mangasan on 2010-01-13
Hope it could be useful

[http://ubuntuforums.org/search.php?searchid=69055592](http://ubuntuforums.org/search.php?searchid=69055592)

I have faced with the same issue after upgrading to Karmic.

cheers

---

### Post by Arctother on 2010-01-19
Hey, running 9.10 Karmic, with Banshee and a 5th Gen 30gb Ipod video.

Banshee was not recognizing the ipod, then I tried
a) plug in ipod (so it automounts)
b) start banshee
c) right click the ipod icon on the desktop, and unmount (not eject or sfely remove)
d) open nautilus and re-mount the ipod.

Voila. Banshee finds it, as does podsleuth. Podsleuth gives an error (Ipod found but is not known) but as long as banshee works, I don't care.

Oh - and I still have Rhythmbox installed, and Banshee will put OGG files on the Ipod. I tried the same fix, both with and without Rockbox installed. Banshee does not seem to know or care what firmware is installed.

Something about the automount seems to confuse Banshee and Podsleuth, so one must manually undo it and redo it.

I know I could turn off automounting, but this is not hard and I do want automounting for other media types.

-Arc

---

### Post by Trinity1976 on 2010-01-20
I'm sorry but what do you mean by 'open nautilus'?

---

### Post by Arctother on 2010-01-21
Nautilus is the name of the graphical file management tool (aka file browser) - you should be able to start it by hitting places - desktop (there are other ways). Then the ipod should appear over in the left hand column, and if you select it, it should mount it.

once mounted, an icon should appear on the desktop, and also in the lefthand column of banshee.

-Arc

---

### Post by LuisGMarine on 2010-01-21
Follow the guide in my signature for a pretty solid fix around for this problem.

---

### Post by mangasan on 2010-01-27
Hi guys,

this issue has been fixed with 1.5.4 version (formerly "1.5.4~really1.5.2-0ubuntu1~hyper2~karmic"). 

The banshee team released it the 21st of January. You can update your Karmic by using the banshee PPA repository as explained here

[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

hth.

cheers.

---

### Post by angheloko on 2010-01-31
The new update helped (I think). But just in case you're still not seeing your iPod, try disabling and enabling the iPod Support. Open up Banshee, go to Edit -> Preference -> Extensions. Untick iPod Support and restart Banshee. (Your iPod shouldn't be mounted at this point otherwise, Banshee just might hang, as it happened to me).

After disabling, re-enable it and now mount your iPod.

HTH

---

### Post by LuisGMarine on 2010-01-31
That sounds good that they fixed it in the recent update.  I just got a fresh install and have not had time to hook up my ipod.

---

### Post by cscott5288 on 2010-02-05
OK, I am having all these same problems. I tried uninstalling musicmatch and I still can't get ipod to appear in Banshee. I am right now trying to install podsleuth but I have no idea how. I found this page: [http://download.banshee-project.org/podsleuth/](http://download.banshee-project.org/podsleuth/) and I downloaded: podsleuth-0.6.6.tar.gz from this page: [http://download.banshee-project.org/podsleuth/LATEST-IS-0.6.6/](http://download.banshee-project.org/podsleuth/LATEST-IS-0.6.6/)

Now, if I did download the correct things to install podsleuth, what do I do after downloading the .gz file? I tried running install-sh in terminal and it changed nothing. There is no install instructions ... just a readme telling me a whole bunch of programmer mumbo jumbo. Any help would be appreciated as I haven't had access to my ipod in months.

---

### Post by cscott5288 on 2010-02-05
> **LuisGMarine said:**
> Follow the guide in my signature for a pretty solid fix around for this problem.

This worked. Thanks.

---

