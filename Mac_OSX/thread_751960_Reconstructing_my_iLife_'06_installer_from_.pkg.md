---
title: "Reconstructing my iLife '06 installer from .pkg"
date: 2008-04-11
forum: Mac OSX
---

### Post by tjniels on 2008-04-11
So, I have an iBook G4 (800 MHz) that I discovered will accept a 1 GB RAM card, bumping the spec from 640 MB to 1154 MB.  Now I may be a glutton for punishment, and I may end up with a very slow machine, but I have decided to spoof the Leopard installer using Open Firmware so I can install it on an "unsupported" machine.  Now don't criticize the idea too quickly, I don't need it to be terrificly fast, I just sense that more and more software developers are focusing their efforts on 10.5.  I am going to scrub the hard drive and install a lean Leopard (leaving out language files and other things I don't need) to be sure I don't max out the poor 30 GB hard drive too quickly.

That being said, I cannot find my old iLife '06 discs.  I know I had them because I installed iLife on the computer a few years ago.  I still have most of the iLife apps, and I have the .pkg file in the "Receipts" folder.  When I open the .pkg, it allows me to reinstall iLife, however, the .pkg is only about 1.5MB.  My goal is to reconstruct the installers from iLife and a few other favorite apps, burn them to CDs, and install them *after* I format my drive and install Leopard.  That way I don't have to dig through boxes to find my old iLife discs, and I don't have to run out and buy iLife '08.  Maybe I'll buy iWork instead!  I have read several forums, and iLife '06 is compatible with Leopard.

I didn't know much about .pkg files before I started trying to figure this out, but here's what I understand so far: a .pkg is full of symbolic links to another spot (or spots) on your hard drive where the actual data required for an installation is found.  I opened the .pkg with "show package contents" from the contextual menu, and found several small resource files and a few aliases–that's all.  Most of the aliases were linking back and forth within the .pkg if I remember correctly, so that didn't really point me to the files I need.

Does anyone know the trick for this?  Starting with a working .pkg file (I say working to indicate that I tried the installer and it works, I just don't know where the actual data is coming from) I need to reconstruct an installer that I can burn to a CD.  Anyone who can, please help!  Thanks in advance.

---

### Post by scramasax on 2008-04-15
> **tjniels said:**
> I still have most of the iLife apps, and I have the .pkg file in the "Receipts" folder.

Except that *isn't* the installation package.  It would waste a fair bit of space on disk if it were.  It's just a BOM -- a Bill Of Materials:

[http://developer.apple.com/documentation/Darwin/Reference/ManPages/man5/bom.5.html](http://developer.apple.com/documentation/Darwin/Reference/ManPages/man5/bom.5.html)

AFAIK, what the Receipts directory does is allow Software Update to check whether an update has been installed or not.  The BOM also gets checked (to see what permissions would have been set on files installed from the package) if you run "Repair Permissions" ... which *pace* ill-informed Mac fan-sites is something you'd only need to do in rare circumstances, and might want to avoid anyway, owing to [privilege escalation issues](http://projects.info-pull.com/moab/MOAB-15-01-2007.html).

In short, if you want to install iLife you'll need to find the discs.  That's just a BOM in /Library/Receipts not the package itself.

---

### Post by tjniels on 2008-04-15
If I were to repair permissions, it would be in this circumstance:

1) I happened to know that I had modified permissions of one or more file(s) or applications(s) and shortly thereafter the system started experiencing problems,
2) I couldn't remember which files I had changed, and
3) I knew that there were no malicious users with root access.

Since I've only had one kernel panic in almost three years on Mac OS X Tiger, somewhere back around 10.4.8, and it fixed itself on reboot and never showed up again (BTW, I think I caused the kernel panic with shoddily-applied system hacks and deleting files that typical users would never find, so I can't blame Apple for this, lol), I have never felt inclined to repair permissions.

OK, OK, OK, several years back when I was new to UNIX I stumbled across "repair permisions" in diskutil once and wondered what it did, and ran it–it didn't change anything noticeable.  Also once when diskutil said my HD on an old computer was failing, I ran "repair permissions" and the HD never failed or showed up as "SMART Status: failing" in diskutil again.  I think that was plain old dumb luck and nothing more.

BUT, since OS X is very stable and can run for years on end with no need to reboot, it seems silly that the feature is so accessible.  I think it should be there, in the same location that it is, but that diskutil itself should be much more carefully guarded.  You are right that the "repair permissions" feature could be exploited, but since I'm the only root user or sys-admin and don't plan to exploit it, everything's cool.  I have a non-root account that I switch to when others want to use my computer.

There are a few things Apple could fix on this, and I'm sure they will in the near future, but I wouldn't bash them too hard–they are bringing UNIX to the masses in a relatively well-packaged and very easy-to-learn format, this is applaudable.  Despite the huge switch from pure proprietary code to a UNIX-based OS, Apple pulled it off smoothly and has maintained it's long-held reputation of being nearly "virus-free".  I won't call OS X perfect, but the UI is beautiful, the learning curve is accommodating for all types of users, and for all the features it has it runs *fast.*  That's all most people can ask for, and they won't find it IMO in any other commercially distributed OS.

But that's not the point of this post, sorry to digress.  I've attached a screenshot of me trying to open the .bom file.  It occurred to me that if I could somehow view the contents of the bill of materials, I could manually collect the necessary files, noting their path names, and manually redistribute them (the same way an installer would manually) in Leopard.  A bit of a stretch, I know, but is there an application that let's me open a .bom and view it?  Thanks for the input, and I probably will look for the discs sooner or later, but that doesn't help me learn anything about the OS or how .pkg and .bom files work.

Oh, and you are correct about the Software Update thing.  For instance, if you wanted to re-install the latest combo updater, you could just delete it's .pkg from the "receipts" folder and run Software Update–I've done it before.

I'd like a little more info on .pkg and .bom files.  Most installers I've seen (that aren't packaged for commercial distribution, that is) contain a .pkg and a folder.  I believe that the .pkg contains a bunch of links to items in the folder, it installs them when you run it.

I tried running the .pkg file for the Danish language files, which I deleted using a tool called Youpi Optimizer (I used it to free up about a gig of disk space).  I wanted to see if the .pkg files in receipts could still run as installers, and it seemed to work OK at first.  I got through the preliminary pages, clicked "start installation", and waited.  The progress bar got to about 10%, then it said there were problems with the installation and asked if I wanted to install again.  So whatever the .pkg linked to cannot be found.

What I'm hoping is that I'll figure out how to read a .bom and then manually locate the files it refers to.  Could this work?

Here's a screenshot to clarify, please offer more suggestions.  I will look for the discs, but this is a general knowledge question as well and would love to figure it out.  Thanks!

---

### Post by scramasax on 2008-04-15
> **tjniels said:**
> You are right that the "repair permissions" feature could be exploited, but since I'm the only root user or sys-admin and don't plan to exploit it, everything's cool.  I have a non-root account that I switch to when others want to use my computer.

I agree that this is a sidetrack.  To start with I only mentioned "Repair Permissions" because that's a main reason for "Receipts" being there, but I couldn't resist adding the *caveat* just because running that when you don't need to has become so prevalent on the Mac.  I shouldn't have got sidetracked.

But I now feel obliged to point out that just because you don't plan to screw up your own computer, doesn't mean something nasty can't happen to it, if you're running with more privileges than are necessary.  Let's take a concrete example on the Mac -- [Oompa Loompa](http://rixstep.com/1/20060216,00.shtml) (also known as Leap-A)

> On 13 February 2006 a post appeared on the MacRumors website promising screen dumps of Apple's upcoming 10.5 Leopard in a file called 'latestpics.tgz'.

The archive contained no graphics - only a worm. Because some people were fooled, the worm can now spread via their iChat clients to other OS X computers.

Preliminary reports say the infection is low (under 50 computers at time of writing) but that's hardly the point.

But Oompa Loompa

> require[d] an admin password if you&#8217;re not running as an admin 

[http://www.macworld.com/article/49440/2006/02/oompa.html](http://www.macworld.com/article/49440/2006/02/oompa.html)

OK, Oompa Loompa was a bit of a damp squib.  Besides, OS X is not Windows 98 -- there's a good level of internal security.  But I think the general point remains -- the bad guys can exploit your level of privilege.

> There are a few things Apple could fix on this, and I'm sure they will in the near future, but I wouldn't bash them too hard&#8211;they are bringing UNIX to the masses in a relatively well-packaged and very easy-to-learn format, this is applaudable.  Despite the huge switch from pure proprietary code to a UNIX-based OS, Apple pulled it off smoothly and has maintained it's long-held reputation of being nearly "virus-free".

I quite agree.  I've noticed that the Windows fans who used to be sheepish at the constant humiliation of the OS at the hands of malware are now getting a little bolder -- and all apparently on the strength of this year's CanSecWest and the one before. :rolleyes:

Now they tell us Vista is the safest OS around.  Preston Gralla just did that at Computerworld.

Fine, if they feel safer.  But in point of fact Vista had to wait till Day 3, because, under the rules, Flash wasn't installed on Day 2.  And, in practice, how many Windows users are likely *not* to have Flash installed?

While I dislike MS, I wouldn't be anything less than fair to them, and AFAICT they have completely changed their attitudes and it would seem that in some respects they're ahead of Apple (and the Linux vendors). However, I suspect they still have some systemic problems -- look at the problems [ActiveX is still causing](http://arstechnica.com/news.ars/post/20080410-report-microsoft-fastest-to-issue-os-patches-sun-slowest.html).  And then there's the question of which target is most attractive to bad guys looking for the most victims.  Sure MS are now making great strides, but in practice one is going to be safer on a Mac or on Linux.

> I won't call OS X perfect, but the UI is beautiful, the learning curve is accommodating for all types of users, and for all the features it has it runs *fast.*

I agree on all points.

>  I've attached a screenshot of me trying to open the .bom file.  It occurred to me that if I could somehow view the contents of the bill of materials, I could manually collect the necessary files, noting their path names, and manually redistribute them

I see.  I hadn't twigged exactly what you were trying to do.  Now Pacifist will handle packages.  AFAIK, it's just a nice GUI for pax, so you could probably use that.  But Pacifist is fairly cheap:

[http://www.charlessoft.com/](http://www.charlessoft.com/)

You can drop packages on there.  And you can use it directly on the BOM inside the package -- I just tried.

---

