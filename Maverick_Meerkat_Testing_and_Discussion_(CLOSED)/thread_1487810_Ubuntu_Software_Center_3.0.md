---
title: "Ubuntu Software Center 3.0"
date: 2010-05-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2010-05-19
Going by this: [https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-software-center-front-end](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-software-center-front-end)

cool things are coming to USC3!

---

### Post by wojox on 2010-05-19
Looks promising. "Where is it" feature sounds good. I don't know how many times a week that question gets asked. :)

---

### Post by ranch hand on 2010-05-19
> **wojox said:**
> Looks promising. "Where is it" feature sounds good. I don't know how many times a week that question gets asked. :)
I don't even like the USC and I think this is just one great idea.  That is one thing that really gets on a noobs thungas for very sure.

---

### Post by cariboo on 2010-05-19
I'm personally not a big fan of the Software Center, Synaptic already has all those features, but I'll wait until the final release before I make a decision.

---

### Post by Slug71 on 2010-05-19
Is Computer Janitor still suppose to be rolled into this?

---

### Post by zekopeko on 2010-05-19
> **Slug71 said:**
> Is Computer Janitor still suppose to be rolled into this?

Doesn't look like it. Neither is the update-manager functionality from what I have seen.

---

### Post by ranch hand on 2010-05-19
> **zekopeko said:**
> Doesn't look like it. Neither is the update-manager functionality from what I have seen.
Update Mangler "functionality" is not needed.

If they want to have USC do updates I think they would be better off to start over on developing that function fresh for USC.

UM is bad enough as it is but adding it as another layer to another app is just asking for trouble.

---

### Post by zekopeko on 2010-05-19
> **ranch hand said:**
> Update Mangler "functionality" is not needed.

If they want to have USC do updates I think they would be better off to start over on developing that function fresh for USC.

UM is bad enough as it is but adding it as another layer to another app is just asking for trouble.

What is wrong with UM?

---

### Post by xebian on 2010-05-19
> **wojox said:**
> Looks promising. "Where is it" feature sounds good. I don't know how many times a week that question gets asked. :)

In Synaptics/details you see where it is. But 99.99% they are in /usr/bin and/or symlink to /usr/lib/ .

---

### Post by Slug71 on 2010-05-19
> **zekopeko said:**
> Doesn't look like it. Neither is the update-manager functionality from what I have seen.

Yeh i actually hope it will remain separate.
Or be replaced with Packagekits variant if PK is chosen as the backend to USC. But still remain separate.

---

### Post by zekopeko on 2010-05-19
> **xebian said:**
> In Synaptics/details you see where it is. But 99.99% they are in /usr/bin and/or symlink to /usr/lib/ .

That doesn't help when I want to know where it is in the menu. Or do you suggest I open /usr/bin with nautilus and look for the app there?

---

### Post by zekopeko on 2010-05-19
> **Slug71 said:**
> Yeh i actually hope it will remain separate.
Or be replaced with Packagekits variant if PK is chosen as the backend to USC. But still remain separate.

Every current packagekit GUI should die a fiery death. Actually PK shouldn't do anything beyond the library/command-line level.

---

### Post by ranch hand on 2010-05-19
> **zekopeko said:**
> Every current packagekit GUI should die a fiery death. Actually PK shouldn't do anything beyond the library/command-line level.
Geeze I hate to disagree with you on that but I really do not think there is any place for packagekit, at least not in package management.

It may well make a great educational tool in Comp Sci classes.  "Hey kids wana see some thing funny?  Heres an example of how not to do package management."

---

### Post by zekopeko on 2010-05-19
> **ranch hand said:**
> Geeze I hate to disagree with you on that but I really do not think there is any place for packagekit, at least not in package management.

It may well make a great educational tool in Comp Sci classes.  "Hey kids wana see some thing funny?  Heres an example of how not to do package management."

PK isn't that bad. As far as I understood, it makes things easier for programmers because if they want to install "some-app" from their application they don't have care for things such as "what distro is this program running", "what package manager" etc and then code a solution for various scenarios only to install "some-app". PK makes this easy because you simply ask it to install "some-app" and it takes care of the rest since it has backends to various package management systems. OTOH I could be wrong on all of this and then I have no clue what problem PK is trying to fix.

The problem is that the GUI used for PK is crap. It suffers from the usual "I'm a programmer but I'm going to create a GUI" syndrome we see all over Linux.

---

### Post by ranch hand on 2010-05-19
I have used it as a user in a couple of distros (Fedora for one).  It is one of the reasons I no longer put them on my box.

The nicest thing I can say about it is that it is clunky and slow.  This could well be the fault of the gui but I have seen three different incarnations of it and want nothing at all to do with it.

---

### Post by zekopeko on 2010-05-19
> **ranch hand said:**
> I have used it as a user in a couple of distros (Fedora for one).  It is one of the reasons I no longer put them on my box.

The nicest thing I can say about it is that it is clunky and slow.  This could well be the fault of the gui but I have seen three different incarnations of it and want nothing at all to do with it.

The slowness could easily be attributed to the historically slow yum. PK doesn't really install stuff. It asks other stuff to install stuff.

---

### Post by ranch hand on 2010-05-19
> **zekopeko said:**
> The slowness could easily be attributed to the historically slow yum. PK doesn't really install stuff. It asks other stuff to install stuff.
That is how I understood it.  Another, unneeded layer and a poor one at that.

---

### Post by null_pointer_us on 2010-05-19
Does USC provide a noob-friendly way to revert from a PPA?

The convenience of meta/virtual packages and PPAs seems to only work one-way.

---

### Post by xebian on 2010-05-19
> **zekopeko said:**
> That doesn't help when I want to know where it is in the menu. 

Don't be looking in the kitchen if you installed a toilet.


```
Or do you suggest I open /usr/bin with nautilus and look for the app there?
```

Whatever is comfortable with you.

---

### Post by zekopeko on 2010-05-19
> **xebian said:**
> Don't be looking in the kitchen if you installed a toilet.


```
Or do you suggest I open /usr/bin with nautilus and look for the app there?
```

Whatever is comfortable with you.

???

---

### Post by seeker5528 on 2010-05-19
> **zekopeko said:**
> PK isn't that bad. As far as I understood, it makes things easier for programmers because if they want to install "some-app" from their application they don't have care for things such as "what distro is this program running", "what package manager" etc and then code a solution for various scenarios only to install "some-app".

It is great for that. That is what the codec installer, 'command not found', and other similar things are. There is a difference between that and package management.  

> The problem is that the GUI used for PK is crap. It suffers from the usual "I'm a programmer but I'm going to create a GUI" syndrome we see all over Linux.

If you are limiting yourself to what PK is capable of, then you are pretty limited in what you can provide in the GUI.

The list of use cases at [http://www.packagekit.org/pk-intro.html](http://www.packagekit.org/pk-intro.html)

> Use cases for PackageKit exist for the following scenarios:

    * Boot time security updates
    * Installing files automatically, e.g. openoffice-clipart
    * Installing new features, e.g. smart-card readers
    * Allowing unprivileged users to install software in a corporate build
    * Opening unknown file formats
    * Removing dependencies for files

The FAQ entry about dependency handling [http://www.packagekit.org/pk-faq.html#dependencies](http://www.packagekit.org/pk-faq.html#dependencies)

> How does PackageKit handle dependencies?

PackageKit does not do dependency resolution. This problem has already been solved by the backend systems and we don't really want to re-invent the wheel.

PackageKit does not have the fine-grained API to do everything. For instance, synaptic should still use libapt as can do much more than can be provided by PackageKit.

So, one place where they indicate what it is designed for, they do not give any indication that it is designed for package management. Then in the FAQ it looks to me like they are saying package managers should not use PK because PK doesn't provide enough control for that.

Gnome-packagekit and kpackage are not what I would call 'package managers' they are more like simple 'add/remove programs' types of things and even for what they provide it seems PK is barely able to handle it.

When you look at USC, sure they want to present a simple 'add/remove' kind of UI to the user, but when you start to look at the list of features it is hoped to have one day, it sounds like even though USC won't be exposing much in the way of management capabilities to the user, USC may need access to a wider range of features that PK provides access to.

I'm not a developer so I can't really say anything definitive about what PK does and doesn't provide relative to what USC needs, but just based on the above quotes from the PK website.....

Why would you think PK should be used in USC?

Later, Seeker

---

### Post by zekopeko on 2010-05-19
> **seeker5528 said:**
> 
Why would you think PK should be used in USC?

Later, Seeker

Where did I say USC should use PK? You have me confused with Slug71. He's the one that has been lobbying for PK to be used in USC for the past two release.

---

### Post by Slug71 on 2010-05-19
> **zekopeko said:**
> Where did I say USC should use USC? You have me confused with Slug71. He's the one that has been lobbying for PK to be used in USC for the past two release.

LOL.

Yes i have. 
But i would just like it to replace aptdaemon. The GUI would stay. Aptdaemon is based on and uses code from PK. The reason aptdaemon was chosen was because of limitations by PK for debconf and conf files. 
This has now been addressed as of PK 0.6.3 i believe, there might still be some backend work to be done if it hasnt already. 
So why not just switch to PK now?

---

### Post by seeker5528 on 2010-05-19
> **zekopeko said:**
> Where did I say USC should use USC?

Sorry about that, I thought it seemed like that was implied somewhere between....

> As far as I understood, it makes things easier for programmers because if they want to install "some-app" from their application they don't have care for things such as "what distro is this program running" and > The problem is that the GUI used for PK is crap.

PK is a daemon.

If you are a programmer and looking for specific files, codecs, clipart, etc... and giving the option to install them from within your program, the GUI is crap thing doesn't really matter, it doesn't take much GUI to create a checkbox or five and an install button either for the group or the individual things. Or in the case where something is missing provide a dialog box asking you if you want to install the package that provides the missing thing.

Since PK doesn't have a GUI, and 'command not found, the codec installer, etc... don't have much UI to complain about, then I think complaints about the GUI must be directed at gnome-packagekit, kpackage or both so I was a little confused about how that fit with the rest......

> **zekopeko said:**
> PK isn't that bad. As far as I understood, it makes things easier for programmers because if they want to install "some-app" from their application they don't have care for things such as "what distro is this program running", "what package manager" etc and then code a solution for various scenarios only to install "some-app". PK makes this easy because you simply ask it to install "some-app" and it takes care of the rest since it has backends to various package management systems. OTOH I could be wrong on all of this and then I have no clue what problem PK is trying to fix.

The problem is that the GUI used for PK is crap. It suffers from the usual "I'm a programmer but I'm going to create a GUI" syndrome we see all over Linux.

Later, Seeker

---

### Post by Slug71 on 2010-05-20
The PK GUI(gnome-packagekit & Kpackagekit) sucks because thats how they are designed. PK is distro/OS neutral and therefore they just provide a GUI that works with the DE(Gnome & KDE).

So to be more clear, packagekit**d** is what would replace aptdaemon and what aptdaemon is based off of.
It is packagekit**d** that is what Packagekit actually is and does what zekopeko has said.

---

### Post by go7Ul1ai on 2010-05-21
Well the update to Software Centre has brought in the history feature and a currently not working  "share via microblog" link in the detailed view of applications :)

---

### Post by dext on 2010-05-22
> **zekopeko said:**
> The slowness could easily be attributed to the **historically slow yum**. PK doesn't really install stuff. It asks other stuff to install stuff. how is Yum so slow? funny i have never found yum to be slow. are you saying apt is faster than yum? got any benchmarks to prove apt is faster than yum

---

### Post by zekopeko on 2010-05-22
> **dext said:**
> how is Yum so slow? funny i have never found yum to be slow. are you saying apt is faster than yum? got any benchmarks to prove apt is faster than yum

Nope. But RPM based distros have always had slow and crappy package management.

---

### Post by dext on 2010-05-22
> **zekopeko said:**
> Nope. But RPM based distros have always had slow and crappy package management.

an apt is so much better than yum?  got anything to back these claims up of yours, both have there pro's an cons.

if RPM package management was so bad.. why is Redhat doing so well in the server an desktop market? ahh yeah, cant forget CentOS either

---

### Post by zekopeko on 2010-05-22
> **dext said:**
> an apt is so much better than yum?  got anything to back these claims up of yours, both have there pro's an cons.

Dude whatever. I'm not going into a <snip> match. Yum and general package management sucked for me the last time I used Fedora.

---

### Post by dext on 2010-05-22
> **zekopeko said:**
> Dude whatever. I'm not going into a pissing match. Yum and general package management sucked for me the last time I used Fedora.
well whenever you last used Fedora/yum it has improved, anyway enough, back on topic

**Note** to the Mods. bad filtering system here if one can see the word <snip> kids use Linux to

this may eventually take over from apt [Cupt a replacement for apt]("http://wiki.debian.org/Cupt")

---

### Post by Slug71 on 2010-05-22
> **dext said:**
> /Cupt"]Cupt a replacement for apt[/URL]

Cupt pretty much just seems like a half rewrite of APT.
If APT is  going to be replaced by anything i hope it is Smartpm.

---

### Post by dext on 2010-05-22
> **Slug71 said:**
> Cupt pretty much just seems like a half rewrite of APT.
If APT is  going to be replaced by anything i hope it is Smartpm.

isnt even finished yet so yeah it is a half rewrite of apt so far. never heard of smartpm till you mentioned it.

---

### Post by Slug71 on 2010-05-22
> **dext said:**
> isnt even finished yet so yeah it is a half rewrite of apt so far. never heard of smartpm till you mentioned it.

Youve probably looked into it already but if you havent:

[http://labix.org/smart](http://labix.org/smart)

Been funded by Canonical since 2005.

---

### Post by dext on 2010-05-23
> **Slug71 said:**
> Youve probably looked into it already but if you havent:

[http://labix.org/smart](http://labix.org/smart)

Been funded by Canonical since 2005.

yeah i took a lot i dont think a lot use it over in fedora.

---

### Post by Slug71 on 2010-05-23
> **dext said:**
> yeah i took a lot i dont think a lot use it over in fedora.

Yeh its still a very quiet little project. Development is also very slow on it but it seems like it has a pretty good concept behind it. 
Works pretty well though. Not so much as the backend to Packagekit though which is how ive been trying to use it. I wish it would be default in Lubuntu and Xubuntu since its more light weight than APT and i think it might really help the project get of the ground but its probably unlikely it will happen. Worst that can happen is revert back to APT. Canonical must have plans for it though.

---

### Post by dext on 2010-05-23
> **Slug71 said:**
> Yeh its still a very quiet little project. Development is also very slow on it but it seems like it has a pretty good concept behind it. 
Works pretty well though. Not so much as the backend to Packagekit though which is how ive been trying to use it. I wish it would be default in Lubuntu and Xubuntu since its more light weight than APT and i think it might really help the project get of the ground but its probably unlikely it will happen. Worst that can happen is revert back to APT. Canonical must have plans for it though.

i tried to find some screenshots of it but i couldnt, just of the GUI whats that like compared to Packagekit

---

### Post by Slug71 on 2010-05-23
> **dext said:**
> i tried to find some screenshots of it but i couldnt, just of the GUI whats that like compared to Packagekit

Totally different compared to PKs GUIs. Its a very simple design.

[http://www.google.com/images?client=ubuntu&channel=fs&q=smart%20package%20manager&oe=utf-8&um=1&ie=UTF-8&source=og&sa=N&hl=en&tab=wi](http://www.google.com/images?client=ubuntu&channel=fs&q=smart%20package%20manager&oe=utf-8&um=1&ie=UTF-8&source=og&sa=N&hl=en&tab=wi)

Take a look at some of the images there from Google. IRC thats what it looked like the last time i installed the smartpm GUI. Packagekit has a smart backend(backend-smart) though and thats how ive been trying to use it. 

Its a neat little tool though. Even in terminal.

Instead of ```
sudo apt-get update
``` or ```
sudo apt-get upgrade
```,

Its just ```
sudo smart update
``` or ```
sudo smart upgrade
``` or ```
sudo smart install xxx
```

---

### Post by LKjell on 2010-05-23
Will there be pinning with the new version of USC?

---

