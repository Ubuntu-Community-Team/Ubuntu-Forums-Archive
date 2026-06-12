---
title: "package managment in mandriva"
date: 2008-06-13
forum: Mandriva/Mageia
---

### Post by pelle.k on 2008-06-13
Hello. I've been running mandriva for a few weeks now, initially because i was fed up with pretty much every gnome distro there is out there for the moment. Let me just say that i think mandriva 2008.1 is hands down one of the very best distributions out there ATM, whether you are an advanced linux user or a linux novice.

However, the fact that mandriva doesn't do dependency based removal of packages you install, means that orphaned packages can pile up quite fast, and that is even worse than cleaning the windows registry after some experimentation with new software (i bet you know what i mean). Sadly the attitude of mandriva developers seem to be that this is complicated and prone to breakage. ( **[http://mandrivausers.org/index.php?showtopic=60894](http://mandrivausers.org/index.php?showtopic=60894)** ) Respectfully, i disagree.
If you keep a record of what is explicitly installed at all times (there is no such mechanism in mandriva), i don't see a problem here. Let me also say that my experience of such auto-removal of dependencies from say debian or arch linux, has not once caused me any trouble, other than when "bad" packages is introduced to the system. Even then, things can be restored.
I hope mandriva will introduce somthing along these lines in the future because honestly, this feels a little bit "1999", and is probably the only "bad" thing i have to say about this otherwise **wonderful** distribution.

---

### Post by pytheas22 on 2008-06-13
Did you consider Kubuntu (or Xubuntu)?  Then you could still have aptitude for package management without the Gnome desktop.  Mandriva (it was my first distribution) is nice but in my experience does a lot of dumb things like you describe.  It was also trying to convince me more often than I liked to buy a subscription.  But to each his own.

---

### Post by pelle.k on 2008-06-13
Oh, i'm your friendly neighborhood distrohopper so i've probably tried every distro on the top 20 of distrowatch during my years with linux. So i'm well aware of what K,X,Ubuntu has to offer me. It's not that i'm fishing for a new distro. Just wanted to bring this to attention. Discuss it :)

---

### Post by logos34 on 2008-06-13
I thought Urpmi was pretty cool until I read this...Has worked smoothly so far. You're kidding--it doesn't have a way to clean up orphaned pkgs/dependencies?  I agree with you about Mandriva in general--it's pretty slick all right, and IMO probably the best distro for migrating windows users to linux (I'm trying to get at least one senior--my 'test' subject--to dual boot it with XP).  If they don't like MandrivaOne 2008.1, then it's probably a lost cause. 

just my 2 cents anyway

---

### Post by pelle.k on 2008-06-14
Well it does some kind of removal on specific packages, like say nautilus. On other, it doesn't.
There's this method of using "rpm-find-leaves", but it is a very basic tool, and it doesn't tell you what packages became orphaned from removing what, and besides that - it's manual work that has do be done.
if i compare rpm-find-leaves before and after i remove a package, thereby pinpoint two "orphans" (they're not orphans really), either one of them can be explicitly installed without me knowing it, because there's no mechanism to show that. So, you may mistakenly remove a critical part of the system, thinking it's a "left over" dependency from a package you deinstalled.
The end result is, only experts can and should deinstall packages this way from the system, leaving "joe user" without a choice.

---

### Post by logos34 on 2008-06-14
wow...that's really discouraging.  The package manager is perhaps the most important part...it's got to be virtually idiot-proof (like apt in ubuntu).  Maybe there's an add-on pkg/gui to do what you're describing?

Not that windows is any better (like you said crap gets left behind in the registry all the time even when you run the 'uninstaller' for a given app).

---

### Post by jrusso2 on 2008-06-14
you can install apt and even synaptic in Mandriva.  So I guess you can do everything you can do with apt in Mandriva.

---

### Post by ffi on 2008-06-14
> **pelle.k said:**
> Hello. I've been running mandriva for a few weeks now, initially because i was fed up with pretty much every gnome distro there is out there for the moment. Let me just say that i think mandriva 2008.1 is hands down one of the very best distributions out there ATM, whether you are an advanced linux user or a linux novice.

However, the fact that mandriva doesn't do dependency based removal of packages you install, means that orphaned packages can pile up quite fast, and that is even worse than cleaning the windows registry after some experimentation with new software (i bet you know what i mean). Sadly the attitude of mandriva developers seem to be that this is complicated and prone to breakage. ( **[http://mandrivausers.org/index.php?showtopic=60894](http://mandrivausers.org/index.php?showtopic=60894)** ) Respectfully, i disagree.
If you keep a record of what is explicitly installed at all times (there is no such mechanism in mandriva), i don't see a problem here. Let me also say that my experience of such auto-removal of dependencies from say debian or arch linux, has not once caused me any trouble, other than when "bad" packages is introduced to the system. Even then, things can be restored.
I hope mandriva will introduce somthing along these lines in the future because honestly, this feels a little bit "1999", and is probably the only "bad" thing i have to say about this otherwise **wonderful** distribution.

from cli *urpmi_rpm-find-leaves* to find them or in *rpmdrake* select to view by leaves and then select packages to uninstall

---

### Post by logos34 on 2008-06-14
> **jrusso2 said:**
> you can install apt and even synaptic in Mandriva.  So I guess you can do everything you can do with apt in Mandriva.
> 
A port of Debian's apt tools for RPM based distributions,
or at least for Mandriva Linux. Original RPM port done by and
for Conectiva. It provides the apt-get utility that
provides a simpler, safer way to install and upgrade packages.
APT features complete installation ordering, multiple source
capability and several other unique features.

Under development, use at your own risk!

It would be nice to use apt instead, which I'm more familiar with.

It says it's 'under development'...any issues to be aware of, or is completely safe to use?

---

### Post by pelle.k on 2008-06-15
> from cli urpmi_rpm-find-leaves to find them or in rpmdrake select to view by leaves and then select packages to uninstall
I'm well aware of the methods and tools to "emulate" dependancy removal in mandriva, but thanks anyway :)
This is a little script i use, that does just the above, but filters out the new leaves for you automatically;
```
#! /bin/sh

remove=${*}

while [ -n "${remove}" ]; do

	# find leaves before removal
	oldleaves=$(urpmi_rpm-find-leaves)
	
	# filter out packages to be removed from oldleaves
	for item in ${remove}; do
		oldleaves=$(echo "${oldleaves}" | sed "s|^${item}$||")
	done

	# remove
	echo  "* remove: "${remove}" ?"
	printf "* (Y/n): "; read answer; [ "${answer}" == "n" ] && exit 1
	[ -n "${remove}" ] && urpme ${remove}

	# find leaves after removal
	newleaves=$(urpmi_rpm-find-leaves)

	# compare old leaves with new leaves, exposing "new" leaves popping up after removal of packages
	remove=$(for package in ${newleaves}; do echo "${oldleaves}" | grep "^${package}$" > /dev/null || echo ${package}; done)
done
```
**You have to be a little careful with it**, since it can do some damage if you have no idea of what you're doing. But in a nutshell, it removes packages with dependancies.
The thing is, there is no mechanism in mandriva to differentiate packages explicitly installed, from packages installed as dependencies, so without that, you cant tell if it's safe to remove a new leaf  - _because you can't tell if it's a leftover dependancy, or in fact a package that is explicitly installed way before it was a dependancy for a certain package_.

---

### Post by AdamWill on 2008-06-16
Honestly, I just don't really see the need for this kind of tool. I mess around with new stuff all the time. I probably have piles of orphan packages on my system. But so what? They're not *doing* anything. They just sit there.

If I run out of disk space (which occasionally happens as I tend to use small root partitions) I just sort packages by size in rpmdrake and remove something big and useless. I don't really care about small packages I don't need any more. Nothing's touching that data. It's just sitting on my disk. I don't lose sleep over it. *shrug*

So...I think this has just never been implemented because we don't really see a deep need for removing orphans. But you can file a bug on urpmi - severity "enhancement" - and see what Pixel thinks.

BTW, there's a significant disadvantage to presenting this kind of tracking and auto-removal as safe, because it's not. Even if no installed package depends on libfoo - so an auto-tracking system would consider it a leave, and remove it - something you've installed some other way might. Something installed from source, or from a binary installer (rather than a package).

---

### Post by pelle.k on 2008-06-16
I think you have a good point Adam. And please note that i'm not bashing mandriva, i'm just focusing on a missing feature.
> BTW, there's a significant disadvantage to presenting this kind of tracking and auto-removal as safe, because it's not. Even if no installed package depends on libfoo - so an auto-tracking system would consider it a leave, and remove it
Yes, and that is why i said my script can be dangerous if you don't know what you're doing. Please note that if i you could tell if a leaf was explicitly installed, or installed as a dependency, this problem wouldn't exist any more.
Maybe you could expand urpmq to reveal install reason, so that those of us wanting to dabble with dependency tracking could do that, even if you don't think it's a feature that fits the mindset of mandriva/urpme?

---

### Post by dca on 2008-06-16
Mandriva's not the only distro that suffers with this issue when it comes to package management.  Ubuntu & Debian use the 'deborphan' (CLI) & 'gtkorphan' (GUI front-end) for complete removal, use at own risk.  OpenSuSE also does not remove packages/libs that are no longer needed.

---

### Post by pelle.k on 2008-06-16
> Ubuntu & Debian use the 'deborphan' (CLI) & 'gtkorphan' (GUI front-end) for complete removal, use at own risk. 
From being an fairly unknown feature, apt-get now does this with "--autoremove". So does aptitude.

---

### Post by AdamWill on 2008-06-16
"Please note that if i you could tell if a leaf was explicitly installed, or installed as a dependency, this problem wouldn't exist any more."

Yep, it would. This is the danger situation:

You install PackagedApp , from the repository
PackagedApp depends on LibFoo0 , so LibFoo0 is installed automatically
You later install NonPackagedApp , from a binary installer, or source, or whatever
NonPackagedApp also uses LibFoo0. Since LibFoo0 is installed, it works fine
You uninstall PackagedApp . The distro helpfully notices that, as far as it knows, LibFoo0 is now an orphan, and offers to remove it. "Sure!", you say.
Oops! Now NonPackagedApp doesn't work, because LibFoo0 is missing.

Yeah, it's a bit of a corner case, but it illustrates that automated leave removal is not entirely safe. As I said, if you feel strongly about this, do file a bug and see what Pixel (urpmi maintainer) thinks. It's ultimately up to him, not me.

---

### Post by pelle.k on 2008-06-16
> Yeah, it's a bit of a corner case, but it illustrates that automated leave removal is not entirely safe.
Yes, you are correct. :)
Thanks for your input, i will take this where it belongs, as suggested.
Thanks!

---

### Post by AdamWill on 2008-06-18
Hey, obviously I know nothing - if you look at the just-released tech specs for 2009 (available from [http://wiki.mandriva.com/en/2009.0_Development](http://wiki.mandriva.com/en/2009.0_Development) ), you'll see that this exact feature is listed there, which means it's a goal for it to be included in 2009 (usually, not everything on the tech specs list actually gets done, but we aim to do as much of it as we can). So yeah, just ignore me in future. :)

---

### Post by pelle.k on 2008-06-18
> you'll see that this exact feature is listed there, which means it's a goal for it to be included in 2009
Oh, how nice! So there's no need for me to file a "bug" then...

> So yeah, just ignore me in future
No, adam. You're the one who let us know about these things, and we truly appreciate your effort. :)

---

### Post by AdamWill on 2008-07-08
Thought you folks might like this:

[root@lenovo libgadu]# urpme --auto-orphans
To satisfy dependencies, the following 2 packages will be removed (95KB):
  
(orphan packages)
  perl-Crypt-OpenSSL-RSA-0.25-3mdv2009.0.i586
  perl-Mail-DomainKeys-1.0-1mdv2009.0.noarch
Remove 2 packages? (y/N) y

Just arrived in Cooker with urpmi 6.0. Will be in 2009 Alpha 2 when it comes out soon. :)

---

