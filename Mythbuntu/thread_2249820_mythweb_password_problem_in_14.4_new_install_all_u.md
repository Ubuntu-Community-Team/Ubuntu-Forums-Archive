---
title: "mythweb password problem in 14.4 new install all updates with repo's"
date: 2014-10-24
forum: Mythbuntu
---

### Post by jeremycobert on 2014-10-24
I just did  a fresh install of 14.4 , enabled the repo's and ran updates. I am now going to setup the mythweb password in the mythbuntu control center ,when i enter a user name and password, click apply (add admin credentials) it run for a second and then this screen comes up. I have no idea what its telling me. can anyone offer tips on this.



[IMG]https://lh3.googleusercontent.com/-6i6Z3B4-xvA/VErWbqn3VeI/AAAAAAAAdE8/LzIOe-VTvMU/w927-h592-no/error.jpg[/IMG]

---

### Post by davefor2 on 2014-11-14
Same issue here 14.04 new install before and after update.
Any help?

Thanks

---

### Post by dannyboy79 on 2014-11-14
i think you have this bug: [https://bugs.launchpad.net/mythbuntu/+bug/1365090](https://bugs.launchpad.net/mythbuntu/+bug/1365090)   do you have all things related to python installed? i'm not certain what exact package you're missing but it looks like you're missing something. The developer of mythbuntu should see this post soon and let you know. just be patient

---

### Post by davefor2 on 2014-11-16
Thanks dannyboy79

---

### Post by Billsputters on 2015-01-06
I have the same problem as well. Does anyone know of a workaround / solution?

---

### Post by Billsputters on 2015-01-10
Is no one else seeing this at all?

Experienced it first as as upgrade from 12.4, so backed up database and did a fresh install, with the same problem.

It's a pain not having the web interface to set recordings and so on

---

### Post by davefor2 on 2015-01-16
I sill have the same issue and just ran updates 01/15/2015
I check Bug #1365090 and it said that it was fixed

                              Marking as Fix Released since we provide newer builds in our PPA and this has been marked fix committed for awhile now.

                               [TABLE="class: bug-activity"]
[TR]
[TD="colspan: 2"]Changed in mythbuntu:[/TD]
[/TR]
[TR]
[TD="align: right"]         **status**:[/TD]
[TD]         Fix Committed &#8594; Fix Released[/TD]
[/TR]
[/TABLE]

Maybe its a different issues.
I am assuming that I am getting the latest updates from the normal software updater. I also have updates from
0.27 repositories checked in Control Center

---

### Post by gweeper on 2015-01-20
I suspect this is a different but similar bug.  I tracked back through Launchpad to find [http://bazaar.launchpad.net/~mythbuntu-dev/mythbuntu/mythbuntu-common/revision/330](http://bazaar.launchpad.net/~mythbuntu-dev/mythbuntu/mythbuntu-common/revision/330)

That is the commit that fixed bug #1365090, and it was only in mythexport.py, but it had to do with the way the config file was opened.

I was trying out a new install earlier today and bumped into this same issue with setting the mythweb password.  I just need to find where mythweb opens it's config file and make the same tweak...

I'll see if I can do this tonight or tomorrow and provide a quick workaround and/or patch.

---

### Post by tgm4883 on 2015-01-21
> **gweeper said:**
> I suspect this is a different but similar bug.  I tracked back through Launchpad to find [http://bazaar.launchpad.net/~mythbuntu-dev/mythbuntu/mythbuntu-common/revision/330](http://bazaar.launchpad.net/~mythbuntu-dev/mythbuntu/mythbuntu-common/revision/330)

That is the commit that fixed bug #1365090, and it was only in mythexport.py, but it had to do with the way the config file was opened.

I was trying out a new install earlier today and bumped into this same issue with setting the mythweb password.  I just need to find where mythweb opens it's config file and make the same tweak...

I'll see if I can do this tonight or tomorrow and provide a quick workaround and/or patch.

You are correct, this is a different issue. Let me take a look.

---

### Post by tgm4883 on 2015-01-23
Looks like there are quite a bit of issues with the mythweb portion of that plugin. It's going to take some time to fix all of them.

---

### Post by Billsputters on 2015-01-28
I've decided to revert back to 12.04, MythWeb can be enabled via MCC and works perfectly.

Problem I now have is that I can not restore the database as the schema from 14.04 is greater than that in 12.04. Anyway to get over this hiccup?

---

### Post by novellahub on 2015-01-28
> **Billsputters said:**
> I've decided to revert back to 12.04, MythWeb can be enabled via MCC and works perfectly.

Problem I now have is that I can not restore the database as the schema from 14.04 is greater than that in 12.04. Anyway to get over this hiccup?

Add the Mythbuntu repos through the  Mythbuntu Control Centre and update Mythtv to the latest version:

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

Then you should be able to restore your database.

---

### Post by Billsputters on 2015-01-28
Came across this, which had fixed MythWeb for me. Happy days

[https://mylinuxramblings.wordpress.com/2014/09/28/mythbuntu-12-04lts-to-14-04-1lts-upgrade/](https://mylinuxramblings.wordpress.com/2014/09/28/mythbuntu-12-04lts-to-14-04-1lts-upgrade/)

---

### Post by Billsputters on 2015-01-29
I was a bit hasty! Certainly MythWeb works and I can now schedule recordings.

But for some reason I can not alter Channel info in the settings tab. Can't change channel number, whether its visible in the FE schedule etc. I think it might be a rights issue, but with what and how I have no idea, and really don't want to tinker for fear of causing further damage!

---

### Post by novellahub on 2015-02-11
> **tgm4883 said:**
> Looks like there are quite a bit of issues with the mythweb portion of that plugin. It's going to take some time to fix all of them.

Any updates on the status of this change?  I recently did a Fresh install of Mythbuntu 14.04.1 migrating hardware to a new setup.  This is the only issue I have left to get sorted out.

---

### Post by tgm4883 on 2015-02-11
> **novellahub said:**
> Any updates on the status of this change?  I recently did a Fresh install of Mythbuntu 14.04.1 migrating hardware to a new setup.  This is the only issue I have left to get sorted out.

My update is I want to stab this code with a knife. This is truly fix 1 bug, 2 more pop up on this plugin. I think I'm going to gut the whole thing. Let me drum up some instructions so you can set the password without the plugin.

---

### Post by Billsputters on 2015-02-16
These instructions found [here]("https://mylinuxramblings.wordpress.com/2014/09/28/mythbuntu-12-04lts-to-14-04-1lts-upgrade/") allow the username and password to be set, so MythWeb works from that point of view. Scheduling programs works fine, however, trying to use the settings tab to alter/edit channel lineups fails as any changes are not written

---

### Post by novellahub on 2015-03-09
> **Billsputters said:**
> These instructions found [here]("https://mylinuxramblings.wordpress.com/2014/09/28/mythbuntu-12-04lts-to-14-04-1lts-upgrade/") allow the username and password to be set, so MythWeb works from that point of view. Scheduling programs works fine, however, trying to use the settings tab to alter/edit channel lineups fails as any changes are not written

Have you tried this solution for editing channels in Mythweb?

[http://ubuntuforums.org/showthread.php?t=2254699&page=2&p=13241447&viewfull=1#post13241447](http://ubuntuforums.org/showthread.php?t=2254699&page=2&p=13241447&viewfull=1#post13241447)

---

