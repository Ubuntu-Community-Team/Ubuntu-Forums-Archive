---
title: "Natty Narwhal a.k.a. 11.04 ... gates are open?"
date: 2010-10-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2010-10-11
I see that folders are open...
Anybody crossed the line on the gate...?

---

### Post by tghe-retford on 2010-10-11
I have:

```
Distributor ID: Ubuntu
Description:    Ubuntu natty (development branch)
Release:        11.04
Codename:       natty
```

Let the breakage begin! :D

---

### Post by zika on 2010-10-11
Of course!> :~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"
> ~$ uname -a
Linux ******* 2.6.36-999-generic #201010100905 SMP Sun Oct 10 09:09:07 UTC 2010 x86_64 GNU/Linux
Enjoy!

---

### Post by Starks on 2010-10-11
I'll stick with 2.6.35 until ndiswrapper works nicely with 2.6.36, but I have the Natty toolchain.

With each dev cycle, the toolchain is getting uploaded faster and faster.

---

### Post by zika on 2010-10-11
We need NN Forum... :)

Just to have a reminder how to cross from MM to NN: [http://www.ubuntu-rs.org/forum/Thread-Kako-pre%C4%87i-na-Natty-Narwhal-a-k-a-11-04-testing?pid=138836#pid138836](http://www.ubuntu-rs.org/forum/Thread-Kako-pre%C4%87i-na-Natty-Narwhal-a-k-a-11-04-testing?pid=138836#pid138836)

---

### Post by Spice Weasel on 2010-10-11
You crazy, crazy people.

Still, this does sound fun. *wants to try*

---

### Post by MacUntu on 2010-10-11
Final for one day was more than enough - let's prepare for a bumpy ride! :D

---

### Post by plun on 2010-10-11
> **tghe-retford said:**
> I have:

```
Distributor ID: Ubuntu
Description:    Ubuntu natty (development branch)
Release:        11.04
Codename:       natty
```

Let the breakage begin! :D


Yup, I am on....:popcorn:

---

### Post by madhi19 on 2010-10-11
You peoples are nuts! lolll

---

### Post by Frogs Hair on 2010-10-11
Captain , there be whales here !

---

### Post by 23dornot23d on 2010-10-11
Its obsessive .... I need something to do through Winter .... hopefully I will be able to follow the prev posted instructions to get the latest and greatest ..... 
or is there a new list of repositories already created ..... to add .....

---

### Post by terry_gardener on 2010-10-11
yes i have crossed the line.
hope i last longer than last time. 

but not bothered now since this time i dual boot.

---

### Post by plun on 2010-10-11
Yes, the gate is open but the toolchain will not be uploaded until Oct 21 according to Nattys schedule

[https://wiki.ubuntu.com/NattyReleaseSchedule](https://wiki.ubuntu.com/NattyReleaseSchedule)

It might break your computer....):P

---

### Post by NCLI on 2010-10-11
I'm on as well. Stable has never been my style :p

---

### Post by MacUntu on 2010-10-11
So, where is "our" forum? :D

---

### Post by seeker5528 on 2010-10-11
> **madhi19 said:**
> You peoples are nuts! lolll

Usually there is not any significant breakage until a month or so into the development.

And since I like to keep both the release and development sources active for the first month or so due to security updates and backports making it into the release repositories quicker I do. 

```
cd /etc/apt
sudo cp sources.list sources.list.d
gksudo gedit sources.list
```

Then using the current stuff as an example change all the references of maverick to natty.

This allows not only to get the newest update from whichever repository has it, but later when development starts gets serious all I have to do is go to the software sources utility or delete '/etc/apt/sources.list.d/sources.list' to dump the old list.

I'm sure somebody has some nifty scripty thingy to update the sources.list, but my scripting skills are deficient and it doesn't take *that* long to edit the sources.list.

Later, Seeker

---

### Post by MacUntu on 2010-10-11
> **seeker5528 said:**
> Usually there is not any significant breakage until a month or so into the development.

Nah, don't say that! I'm sure Debian import brings some fun:

[https://lists.ubuntu.com/archives/maverick-changes/2010-May/thread.html](https://lists.ubuntu.com/archives/maverick-changes/2010-May/thread.html)

:biggrin:

---

### Post by 23dornot23d on 2010-10-11
Sounds good to me .... ready as I will ever be ....
> 
keith2@keith-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"
keith2@keith-laptop:~$ 



I will edit a file and change all the names to natty and have it on standby ...... ty .... :)

---

### Post by DoeRayMe on 2010-10-11
Im ready :D

> :~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"


---

### Post by Starks on 2010-10-11
Guys, I'd recommend keeping your maverick-updates repo.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe

---

### Post by seeker5528 on 2010-10-11
> **MacUntu said:**
> Nah, don't say that! I'm sure Debian import brings some fun:

[https://lists.ubuntu.com/archives/maverick-changes/2010-May/thread.html](https://lists.ubuntu.com/archives/maverick-changes/2010-May/thread.html)

There is the normal 'I allowed a partial update now blah blah blah' type stuff, but as far as the packages themselves causing breakage, usually the big stuff is caught and the Debian and other upstream packages have not yet had that much time to drift from what was in the stable release.

That's not to say there isn't breakage during that time, just that it's usually not going to be more significant type breakage you might see after 2+ months into it when there is more variance in software between the release and development versions, patches start having to be re-worked and work on Ubuntu specific stuff is picking up a little more.

As far as the stuff pulled in from Debian is concerned, it may be even less of an issue this time around because of the state of freeze they are in for the upcoming Debian Squeeze release. 

Later, Seeker

---

### Post by celticbhoy on 2010-10-11
What the hell, I'm in :D

Missed most of 10.10, as I lost internet at work for a while, and although I would update at home every couple of days, I wasn't active enough to feel part of it.

But its back now and I cant wait.

---

### Post by danbuter on 2010-10-11
If nothing else, Natty should be extra stable due to 3 weeks extra dev time.

---

### Post by cariboo on 2010-10-12
> **danbuter said:**
> If nothing else, Natty should be extra stable due to 3 weeks extra dev time.

No it means more time to add several cool features, if natty is more stable than maverick, it'll be pretty boring. :)

---

### Post by donniezazen on 2010-10-12
How do i upgrade to Natty?

---

### Post by zika on 2010-10-12
> **soham_1207 said:**
> How do i upgrade to Natty?
[http://www.ubuntu-rs.org/forum/Thread-Kako-pre%C4%87i-na-Natty-Narwhal-a-k-a-11-04-testing?pid=138836#pid138836](http://www.ubuntu-rs.org/forum/Thread-Kako-pre%C4%87i-na-Natty-Narwhal-a-k-a-11-04-testing?pid=138836#pid138836)

---

### Post by zika on 2010-10-12
First "breakage": In Synaptic- no way to change repository list... :)

---

### Post by zika on 2010-10-12
> **Starks said:**
> Guys, I'd recommend keeping your maverick-updates repo.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe

Do You think that by keeping```
deb http://archive.ubuntu.com/ubuntu/ maverick-updates main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ maverick-proposed main restricted multiverse universe 
deb http://archive.ubuntu.com/ubuntu/ maverick-backports main restricted multiverse universe 
deb http://archive.ubuntu.com/ubuntu/ maverick-security main restricted multiverse universe 

```for the time being until toolchain get running, I could get into trouble. I.E. are the version # for the packages going to get in the right order?

---

### Post by MacUntu on 2010-10-12
Correct me if I'm wrong, but the toolchain is already uploaded.

[https://lists.ubuntu.com/archives/natty-changes/2010-October/thread.html](https://lists.ubuntu.com/archives/natty-changes/2010-October/thread.html)

---

### Post by zika on 2010-10-12
> **MacUntu said:**
> Correct me if I'm wrong, but the toolchain is already uploaded.

[https://lists.ubuntu.com/archives/natty-changes/2010-October/thread.html](https://lists.ubuntu.com/archives/natty-changes/2010-October/thread.html)
I know that. I was not precise.

---

### Post by DougieFresh4U on 2010-10-12
Of course I have jumped in.
Only had a couple issues last round, nothing that was 'show' stopping. Getting easier with each release. :(

---

### Post by bash on 2010-10-12
And I was just wondering how long it took for the first Natty thread to show up. Thought it would take a couple more days. It's like a gathering of addicts. Must. Not. Use. Stable. Version.

Anyway will probably jump on around Alpha 1. 'Till then got the GNOME Shell jhbuild to keep me happy with breakage.

---

### Post by zika on 2010-10-12
> **bash said:**
> And I was just wondering how long it took for the first Natty thread to show up. Thought it would take a couple more days. It's like a gathering of addicts. Must. Not. Use. Stable. Version.

Anyway will probably jump on around Alpha 1. 'Till then got the GNOME Shell jhbuild to keep me happy with breakage.

We'll be here, waiting... :)
If we get a Forum, we'll go there...

---

### Post by donniezazen on 2010-10-12
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release](http://linux.dropbox.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Simian Man on 2010-10-12
Ubuntu is never *that* unstable.  Try Debian Unstable, Fedora Rawhide or Arch Testing for some real fun.

---

### Post by zika on 2010-10-12
New NN Forum is being just opened.
Nice!

---

### Post by Joeb454 on 2010-10-12
I've just created it - only appears if you're connected to Lingonberry though (check the bottom of any UF page to check which server you're on). I've notified the Canonical guys to fix the issue, hopefully it'll be sorted soon!

---

### Post by donniezazen on 2010-10-12
> **Simian Man said:**
> Ubuntu is never *that* unstable.  Try Debian Unstable, Fedora Rawhide or Arch Testing for some real fun.

I can't remember if i had to reinstall maverick due to crash.

---

### Post by 23dornot23d on 2010-10-12
Nice script showing useful sources ..... I like it ..... 

ty for posting Framli ...... [LINK]("http://ubuntuforums.org/showthread.php?p=9955603#post9955603")

Although does not look good ..... only 4 out of 82 .... are any good ..... for me at the moment.

[IMG]http://img707.imageshack.us/img707/5452/snapshot3jq.jpg[/IMG]

I have been having a [good test of Gnome Shell]("https://sites.google.com/site/000menu/home/gnome---3/gnome-shell") too and I like it ...... its growing on me ...... ;)

I still think there are some more modules I need for it though .... 

I wonder where they are and how to activate the full set  !!!

---

### Post by zika on 2010-10-12
> **Joeb454 said:**
> I've just created it - only appears if you're connected to Lingonberry though (check the bottom of any UF page to check which server you're on). I've notified the Canonical guys to fix the issue, hopefully it'll be sorted soon!Thank You!
If You could it would be nice to move this thread in that Forum, where it belongs...

---

### Post by 23dornot23d on 2010-10-12
Only do it (change the thread location of this one) when we can all access it though ..... please ..... 

I cannot see the new one for (Natty) yet ..... do you have a direct link that we can try ....... ty

---

### Post by 98cwitr on 2010-10-12
no kernel update...no care

---

### Post by donniezazen on 2010-10-12
> **23dornot23d said:**
> Nice script showing useful sources ..... I like it ..... 

ty for posting Framli ...... [LINK]("http://ubuntuforums.org/showthread.php?p=9955603#post9955603")

Although does not look good ..... only 4 out of 82 .... are any good ..... for me at the moment.

[IMG]http://img707.imageshack.us/img707/5452/snapshot3jq.jpg[/IMG]

I have been having a [good test of Gnome Shell]("https://sites.google.com/site/000menu/home/gnome---3/gnome-shell") too and I like it ...... its growing on me ...... ;)

I still think there are some more modules I need for it though .... 

I wonder where they are and how to activate the full set  !!!

Last time i checked you can't use dock in Gnome-shell. What docks are you using?

---

### Post by donniezazen on 2010-10-12
> **zika said:**
> First "breakage": In Synaptic- no way to change repository list... :)

Yeah can't open repository or command line.

> sudo add-apt-repository ppa:ricotz/testing
[sudo] password for donnie: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 55, in <module>
    sp = SoftwareProperties()	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template


---

### Post by 23dornot23d on 2010-10-12
> **soham_1207 said:**
> Last time i checked you can't use dock in Gnome-shell. What docks are you using?

I can use both [docky and cairo-dock]("http://www.youtube.com/watch?v=EYbqsKPV9mg&feature=player_embedded") ..... they work ok in the version of Gnome3 I have

I start gnome-shell --replace

docky runs from the startup applications as does gnome-shell --replace

[B][COLOR=Red]but to run Cairo-Dock ...... you have to start it manually afer everything else ..... otherwise you lose the effects ........
[/COLOR][/B]
Also just getting used to using it .... so having to do keystrokes as Gtk Recordmydesktop uses the top line and the mouse will not pick Gnome3

Alt and Alt Tab are useful though .......

( Gtk Recordmydesktop ...... flickers the top bar a bit - too .... not sure why !!!! )

 ...........   I have no idea how to tell which version of Gnome3 it is or what modules are running  ..... there is no **About .**.....

I compiled it from the latest source files as far as I know .... [_look here for what I did_]("http://ubuntuforums.org/showthread.php?t=1476241&page=84")

[B]GNOME3 could do with a small screen .. just showing some basic details of version modules working etc ....
[/B]

---

### Post by 23meg on 2010-10-12
> **23dornot23d said:**
> they work ok in the version of Gnome3 I have

> **23dornot23d said:**
> the mouse will not pick Gnome3

> **23dornot23d said:**
>  ...........   I have no idea how to tell which version of Gnome3 it is or what modules are running  ..... 

> **23dornot23d said:**
> **GNOME3 could do with a small screen .. **

You're running GNOME Shell, not GNOME 3. GNOME Shell is one part of what is to become the initial GNOME 3 release.

---

### Post by ranch hand on 2010-10-12
All I can say is that anyone getting into 11.04 at this time should have no trouble with the stability of the OS anytime during testing.  The OS will always be more stable than the person in the chair.

I took a look at my lsb-release file and it says;
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

```

---

### Post by 23dornot23d on 2010-10-12
Sorry forgive me ..... 

I say Gnome3 out of habit .... as that is the desktop option that  I choose GNOME3
before initiating 

**gnome-shell --replace**

so does this mean .......... I am not running GNOME3 then ....... 

I am running GNOME-SHELL ...... in GNOME3 as far as I know .....

I get confused .... I am getting OLD now ......  :(

Good to see you back Ranch Hand ...... love the humour .... ;)
( its only the crazy people that keep this all sane  )

( Gnome Shell just seems to be a part of the build ...... when using jhbuild .... how do we know what anything is where is the About ?)

---

### Post by bash on 2010-10-12
> **98cwitr said:**
> no kernel update...no care

You could always grab 2.6.36 from the kernel-mainline ppa

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Starks on 2010-10-12
> **zika said:**
> Do You think that by keeping```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed main restricted multiverse universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports main restricted multiverse universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security main restricted multiverse universe 

```for the time being until toolchain get running, I could get into trouble. I.E. are the version # for the packages going to get in the right order?
For the first week or so, until Debian imports begin, maverick-updates should supersede natty-main in versioning.

---

### Post by 23meg on 2010-10-12
> **23dornot23d said:**
> 
so does this mean .......... I am not running GNOME3 then ....... 

Yes, since strictly speaking, GNOME 3 does not exist yet. 

This is GNOME Shell: [http://live.gnome.org/GnomeShell/](http://live.gnome.org/GnomeShell/)

This is GNOME 3: [http://live.gnome.org/ThreePointZero](http://live.gnome.org/ThreePointZero)

You do need pre-release versions of some components that will be part of GNOME 3 as build dependencies, which is why they're being fetched when *jhbuild*ing.

---

### Post by 23dornot23d on 2010-10-12
Cheers .....  for the links ...... 

I have just started as you can probably tell .... so just dipping my feet in the water so to speak ....

So then its Gnome-Shell that needs a little pop up .... showing its version .....   

and then we all are in no doubt of what we are running ...... ty

---

### Post by donniezazen on 2010-10-12
> **23dornot23d said:**
> I can use both [docky and cairo-dock]("http://www.youtube.com/watch?v=EYbqsKPV9mg&feature=player_embedded") ..... they work ok in the version of Gnome3 I have

I start gnome-shell --replace

docky runs from the startup applications as does gnome-shell --replace

[B][COLOR=Red]but to run Cairo-Dock ...... you have to start it manually afer everything else ..... otherwise you lose the effects ........
[/COLOR][/B]
Also just getting used to using it .... so having to do keystrokes as Gtk Recordmydesktop uses the top line and the mouse will not pick Gnome3

Alt and Alt Tab are useful though .......

( Gtk Recordmydesktop ...... flickers the top bar a bit - too .... not sure why !!!! )

 ...........   I have no idea how to tell which version of Gnome3 it is or what modules are running  ..... there is no **About .**.....

I compiled it from the latest source files as far as I know .... [_look here for what I did_]("http://ubuntuforums.org/showthread.php?t=1476241&page=84")

[B]GNOME3 could do with a small screen .. just showing some basic details of version modules working etc ....
[/B]

There has not been much growth in Gnome-shell viz. customization. Is it going to be default GUI in Naughty.

---

### Post by zika on 2010-10-12
This is how we started NN testing season...
[http://ubuntuforums.org/showthread.php?t=1593270](http://ubuntuforums.org/showthread.php?t=1593270)

---

### Post by paul_in_london on 2010-10-12
I'm finally in!

My PC has been dead for 3 weeks. Tried replacing the power supply. Still no good, but I've now managed to get hold of an older machine that I can use in the meantime until I get mine fixed. I have to use xubuntu because it's low spec.

Oh well...

---

### Post by jerrylamos on 2010-10-12
> **paul_in_london said:**
> I'm finally in!

My PC has been dead for 3 weeks. Tried replacing the power supply. Still no good, but I've now managed to get hold of an older machine that I can use in the meantime until I get mine fixed. I have to use xubuntu because it's low spec.

Oh well...
Paul,
I've been having fun with Lubuntu.  It has a lower spec than Xubuntu.  It uses LXDE as a desktop, small and fast and has all the functions I need, and by default Chromium for a browser.  You could put on Firefox 4 if you want.  I'm entering this from Lubuntu 10.10.10 based on Ubuntu 10.10.10 without a lot of the slow disk hungry stuff.

From developer Julien Lavergne:

" Lubuntu 10.10 is now available :

 * Torrent : [http://people.ubuntu.com/~gilir/lubuntu-10.10.iso.torrent](http://people.ubuntu.com/~gilir/lubuntu-10.10.iso.torrent)
 * Direct download : [http://people.ubuntu.com/~gilir/lubuntu-10.10.iso](http://people.ubuntu.com/~gilir/lubuntu-10.10.iso)
 * Md5: [http://people.ubuntu.com/~gilir/md5sum.txt](http://people.ubuntu.com/~gilir/md5sum.txt)

== What is Lubuntu ? ==

Lubuntu is an Ubuntu derivated using the LXDE desktop. It's designed to
be a lightweight and easy-to-use desktop environment.

Lubuntu is actually not part of the Ubuntu family, and not build with
the current Ubuntu infrastructure. This release is considered as a «
stable beta », a result that could be a final and stable release if we
was included in the Ubuntu family.

== Features ==

 * Based on the lightweight LXDE desktop environment.
 * Pcmanfm 0.9.7, a fast and lightweight files manager using gio/gvfs.
 * Lxdm, a lightweight GTK display manager.
 * Chromium, the open-source version of Google Chrome.
 * ... and, of course, based on Ubuntu 10.10

See the complete list of applications on
https://wiki.ubuntu.com/Lubuntu/Applications"

While not officially supported by Ubuntu, the usual updates from the Ubuntu repositories work so you can keep up with Maverick 10.10.10 changes.

Have fun, Jerry

---

### Post by 23dornot23d on 2010-10-12
This was posted on the Meerkat Site as regards [Gnome 3 ...... for March 2011]("http://mail.gnome.org/archives/devel-announce-list/2010-July/msg00003.html")

There is now another 5 to 6 months for developing it .... a lot can change in 5 to 6 months.

Hopefully some other things will be released too ..... ;)

---

### Post by ubunterooster on 2010-10-12
I am soo ready, I've been bored of 10.10 for months it seems

[COLOR=Lime]ubunterooster@mountaindew:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"
[/COLOR][COLOR=Lime]ubunterooster@mountaindew:~$ [/COLOR]

---

### Post by autocrosser on 2010-10-12
AVAST ALL!!!!  I be in!!!  "normally" what I do for the first couple of weeks is run a dual sources list--keep the "old" system list & add the "new" one--you do need to monitor your updates very closely doing this--as soon as the "new" stuff gets rolling well you drop the "old" sources (generally about 2~3 weeks after UDS)

I will be seeing all of you 'round the narwhal soon!!!!!

---

### Post by autocrosser on 2010-10-12
ARRRR!!! Avast all ye maties!!!!  I be in!


FROM THE "OTHER" THREAD-----

AVAST ALL!!!!  I be in!!!  "normally" what I do for the first couple of  weeks is run a dual sources list--keep the "old" system list & add  the "new" one--you do need to monitor your updates very closely doing  this--as soon as the "new" stuff gets rolling well you drop the "old"  sources (generally about 2~3 weeks after UDS)

I will be seeing all of you 'round the narwhal soon!!!!!

---

### Post by ubunterooster on 2010-10-12
I've been bored w/ 10.10 for a long time. I hope this release is more exciting! :D

---

### Post by jerrylamos on 2010-10-12
> **ubunterooster said:**
> I've been bored w/ 10.10 for a long time. I hope this release is more exciting! :D
There are some variants to boring 10.10 example Lubuntu & Firefox 4.0.  

A couple of my pc's have intel video graphics which has been anything but boring, and even ati Mobility 7500 had some fits with 10.10 when booting with an external monitor and settings set to Thinkpad laptop monitor off.

Jerry

---

### Post by karmila on 2010-10-12
My first testing was Maverick and now can't wait for Natty :)

---

### Post by autocrosser on 2010-10-12
Welcome to the "crazy" group.....be wary--the seas may be a bit rough in a month or so.....

---

### Post by zika on 2010-10-12
[http://ubuntuforums.org/showthread.php?t=1594787](http://ubuntuforums.org/showthread.php?t=1594787)

---

### Post by 23dornot23d on 2010-10-13
In at last ..... alls good again ..... ;)

---

### Post by PaulReaver on 2010-10-13
narwhals... [[COLOR="Red"]here[/COLOR]]("http://www.weebls-stuff.com/songs/Narwhals/")

---

### Post by arpanaut on 2010-10-13
Now, That's Funny!

---

### Post by PaulReaver on 2010-10-13
yeah weebls stuff rocks
You should watch the weebl and bob cartoons, epic funny...  



how would we nominate a package to be packaged?  or re-packaged?

I think nexuiz should be a meta package that pulls in a 'darkplaces' package.
nexuiz uses the standard darkplaces anyway.... just renamed.
but this way would make it far easier for noobs to install quake, and nexuiz would obviously still work....

---

### Post by autocrosser on 2010-10-13
> **23dornot23d said:**
> In at last ..... alls good again ..... ;)

Feels good to have a /home again ;)

---

### Post by meborc on 2010-10-13
will join the fun with my netbook this time... have to keep my lappy functional :)

---

### Post by taavikko on 2010-10-13
> **meborc said:**
> will join the fun with my netbook this time... have to keep my lappy functional :)

It's all or nothing...
sources are pointing towards Natty since last night.

---

### Post by zika on 2010-10-13
> **taavikko said:**
> It's all or nothing...
sources are pointing towards Natty since last night.Good choice. Full speed ahead!

---

### Post by autocrosser on 2010-10-13
Batton th' hatches!!! Narwhals be 'head!!!!!

---

### Post by ubunterooster on 2010-10-13
> **autocrosser said:**
> Feels good to have a /home again ;)
this, also how long till the fun really starts! December? :(

---

### Post by xebian on 2010-10-13
Now that 10.10 is out is 11.11 a possibility? Or even better 12.12 just to appease 6-month release critics.  :)

---

### Post by ubunterooster on 2010-10-13
no 11.11 or 12.12 will ever exist

---

### Post by scradock on 2010-10-13
OK, I'm in too!

BUT - I tried using "update-manager -d", and it had no effect.

I had to hand-edit the sources.list file, which I learned NOT to do a couple of releases ago - I remember that I had to also edit some other file as well.

Using either Main or US servers....

Any insights? Anything else I should do to clean up and prevent future problems (apart from the FUN)?

---

### Post by jerrylamos on 2010-10-13
> **scradock said:**
> OK, I'm in too!

BUT - I tried using "update-manager -d", and it had no effect.

I had to hand-edit the sources.list file, which I learned NOT to do a couple of releases ago - I remember that I had to also edit some other file as well.

Using either Main or US servers....

Any insights? Anything else I should do to clean up and prevent future problems (apart from the FUN)?
0. I always have more than one partition of maverick or lucid so I always have something that boots.  In a maverick test install partition - 6 gb will do nicely:
1. Make sure you're up to date:
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude safe-upgrade
2. Save a copy of sources.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list.d
3. Use linux command to edit sources.list:
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list
4. Check to make sure:
less /etc/apt/sources.list
5. Do the update.  Using formal Debian type of install here.
sudo aptitude update
sudo aptitude install dpkg aptitude get

Reboot and see what happened.   "Worked for me ...."

Now I don't use "update manager" or "synaptic" because I've been burned several times by the dread "partial upgrade".  aptitude safe-upgrade hasn't had that problem with me.

I also don't like apt-get dist-upgrade either because I've had a couple installs absolutely destroyed by apt-get.

Enjoy....
Jerry

---

### Post by ranch hand on 2010-10-13
> **scradock said:**
> OK, I'm in too!

BUT - I tried using "update-manager -d", and it had no effect.

I had to hand-edit the sources.list file, which I learned NOT to do a couple of releases ago - I remember that I had to also edit some other file as well.

Using either Main or US servers....

Any insights? Anything else I should do to clean up and prevent future problems (apart from the FUN)?
In the sticky on the 11.04 release there is an explanation of why Update Mangler will not work yet.  It will be happy to mangle your upgrade after A1.

---

### Post by Vanishing on 2010-10-13
upgrading..:)..lets see how long i can go without reinstalling.

---

### Post by autocrosser on 2010-10-13
> **ubunterooster said:**
> this, also how long till the fun really starts! December? :(

Well--I would guess about a couple of weeks after UDS is over----The sooner---THE BETTER!!!

OK Everyone>>>>>>>[SIZE=2]LET THE BREAKAGE BEGIN!!![/SIZE]

---

### Post by ubunterooster on 2010-10-13
> **autocrosser said:**
> Well--I would guess about a couple of weeks after UDS is over----The sooner---THE BETTER!!!

OK Everyone>>>>>>>[SIZE=2]LET THE BREAKAGE BEGIN!!![/SIZE]
Yes!

---

### Post by plun on 2010-10-13
Heya....

```
plun@plun-laptop:~$ uname -a
Linux plun-laptop 2.6.36-0-generic #1-Ubuntu SMP Wed Oct 13 10:58:03 UTC 2010 x86_64 GNU/Linux
```

The first 2.6.36 kernel from Ubuntu....;)

---

### Post by Vanishing on 2010-10-13
Finally:
```
vanishing@Vanishing:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"
```

---

### Post by paul_in_london on 2010-10-13
> **jerrylamos said:**
> Paul,
I've been having fun with Lubuntu.  It has a lower spec than Xubuntu.  It uses LXDE as a desktop, small and fast and has all the functions I need, and by default Chromium for a browser.  You could put on Firefox 4 if you want.  I'm entering this from Lubuntu 10.10.10 based on Ubuntu 10.10.10 without a lot of the slow disk hungry stuff.

From developer Julien Lavergne:

" Lubuntu 10.10 is now available :

 * Torrent : [http://people.ubuntu.com/~gilir/lubuntu-10.10.iso.torrent](http://people.ubuntu.com/~gilir/lubuntu-10.10.iso.torrent)
 * Direct download : [http://people.ubuntu.com/~gilir/lubuntu-10.10.iso](http://people.ubuntu.com/~gilir/lubuntu-10.10.iso)
 * Md5: [http://people.ubuntu.com/~gilir/md5sum.txt](http://people.ubuntu.com/~gilir/md5sum.txt)

== What is Lubuntu ? ==

Lubuntu is an Ubuntu derivated using the LXDE desktop. It's designed to
be a lightweight and easy-to-use desktop environment.

Lubuntu is actually not part of the Ubuntu family, and not build with
the current Ubuntu infrastructure. This release is considered as a «
stable beta », a result that could be a final and stable release if we
was included in the Ubuntu family.

== Features ==

 * Based on the lightweight LXDE desktop environment.
 * Pcmanfm 0.9.7, a fast and lightweight files manager using gio/gvfs.
 * Lxdm, a lightweight GTK display manager.
 * Chromium, the open-source version of Google Chrome.
 * ... and, of course, based on Ubuntu 10.10

See the complete list of applications on
https://wiki.ubuntu.com/Lubuntu/Applications"

While not officially supported by Ubuntu, the usual updates from the Ubuntu repositories work so you can keep up with Maverick 10.10.10 changes.

Have fun, Jerry

Thanks Jerry. 

I've tried Lubuntu/LXDE before actually, but I forgot about it when I decided to install Xubuntu on this machine. I still prefer Gnome though so I hope I can get my main machine fixed soon! :)

---

### Post by jerrylamos on 2010-10-13
> **Vanishing said:**
> upgrading..:)..lets see how long i can go without reinstalling.
reinstall does test the install process.  That way we can write bugs to get fixed.

Also from my experience upgrades upon upgrades gradually increase the disk space usage, and a reinstall at the same level saves space.  I don't know why this occurs.  I do clean up etc.

Alpha's & Beta's do blow up from time to time, so reinstall keeps "how to do it" fresh.

Oh, yes, on this pc there's 10 Ubuntu images at various stages from karmic to lucid to Lubuntu to ... so if one blows up I can do a rescue.  I've even salvaged an image by doing chroot....

Jerry

---

### Post by donniezazen on 2010-10-13
Since software sources is not working i appended sources.list and tried to add the key using command line. I get following error.

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7


---

### Post by scradock on 2010-10-13
> **ranch hand said:**
> In the sticky on the 11.04 release there is an explanation of why Update Mangler will not work yet.  It will be happy to mangle your upgrade after A1.
Thanks, ranch hand - that explains it.

---

### Post by zika on 2010-10-14
After some trimming and modifications, I have:```
deb http://archive.ubuntu.com/ubuntu/ natty main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse 
# deb http://archive.ubuntu.com/ubuntu/ natty-proposed main restricted universe multiverse 
# deb http://archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse 
deb http://archive.canonical.com/ubuntu natty partner
deb http://deb.opera.com/opera-beta/ testing non-free
# deb http://deb.opera.com/opera/ lenny non-free
```as my /etc/apt/sources.list. Did I miss something...?
Of course, Xorg-Edgers, MozillaDaily and others are in /etc/sources.list.d/... Ready for natty>maverick turnover...

---

### Post by moviemaniac on 2010-10-14
Sources for nutritious narcotics have been set since sunday :D

Another release cycle, another few months of testing goodness :)

---

### Post by zika on 2010-10-14
> **plun said:**
> Heya....

```
plun@plun-laptop:~$ uname -a
Linux plun-laptop 2.6.36-0-generic #1-Ubuntu SMP Wed Oct 13 10:58:03 UTC 2010 x86_64 GNU/Linux
```

The first 2.6.36 kernel from Ubuntu....;)Did You get it direct?
I'm not getting it, yet, in update/upgrade process...

P.S. Yes, I can see it in Synaptic, it is waiting for dummy packages... OK... 2.6.36-2 is current and 3 is building...

---

### Post by jerrylamos on 2010-10-14
> **ranch hand said:**
> In the sticky on the 11.04 release there is an explanation of why Update Mangler will not work yet.  It will be happy to mangle your upgrade after A1.

Mangle is right!  "Update Manager" has manngled so bad I had to re-install.  apt-get destroyed Maverick on two pc's in August same way. Broken so bad that fix broken packages didn't work.  Chroot into the busted ubutu partly worked but best way was to wipe out and re-install.

Safest quickest way for me to update is in a terminal session:
Note: if aptitude not installed, do sudo apt-get install aptitude

gedit up (or whatever name you'd like)

#! /bin/bash
sudo aptitude update
sudo aptitude safe-upgrade
exit #

save
sudo chmod 777 up

test it:

./up

if O.K., then

sudo cp up /usr/bin

Thereafter just enter in a terminal session:

up

to update each day....whole lot faster with less keystrokes than update manager.  

Good luck, Jerry

---

### Post by taavikko on 2010-10-14
> **jerrylamos said:**
> 
Safest quickest way for me to update is in a terminal session:
Note: if aptitude not installed, do sudo apt-get install aptitude

gedit up (or whatever name you'd like)

#! /bin/bash
sudo aptitude update
sudo aptitude safe-upgrade
exit #

save
sudo chmod 777 up

test it:

./up

if O.K., then

sudo cp up /usr/bin

Thereafter just enter in a terminal session:

up

to update each day....whole lot faster with less keystrokes than update manager.  

Good luck, Jerry

Too much hassle...

just add an alias to .bash_aliases
alias upgrade='sudo aptitude update && sudo aptitude safe-upgrade'
and source .bashrc

---

### Post by lidex on 2010-10-14
Thought I could stay away for a week or two...feel like an addict.
```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"
```

---

### Post by Framli on 2010-10-14
alias up='sudo aptitude update && sudo aptitude safe-upgrade' in .bash_aliases, is the first thing I do after any install.

...after sudo apt-get aptitude of course.

---

### Post by ubunterooster on 2010-10-14
> **lidex said:**
> Thought I could stay away for a week or two...feel like an addict.
```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"
```
Don't we all

;P

---

### Post by 23dornot23d on 2010-10-14
As a answer to Post #88

@ SOHAM_1207

> **soham_1207 said:**
> Since software sources is not working i appended sources.list and tried to add the key using command line. I get following error.

> 
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  maverick Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
Try it like this ... works for me ......  for the wine one at least .....



keith@keith-laptop:~$ **gpg --keyserver hkp://keyserver.ubuntu.com:11371 --recv-key 5A9A06AEF9CB8DB0**
gpg: directory `/home/keith/.gnupg' created
gpg: new configuration file `/home/keith/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/keith/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/keith/.gnupg/secring.gpg' created
gpg: keyring `/home/keith/.gnupg/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /home/keith/.gnupg/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
keith@keith-laptop:~$ **gpg -a --export 5A9A06AEF9CB8DB0 | sudo apt-key add -**
[sudo] password for keith: 
OK
keith@keith-laptop:~$

---

### Post by Iowan on 2010-10-14
Threads merged... :)

---

### Post by zika on 2010-10-15
Thank You!

---

### Post by linuxman94 on 2010-10-17
I am up!

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

```

---

### Post by plun on 2010-10-18
Today we have Nattys first 2.6.36 kernel....

> linux-meta (2.6.36.0.1) natty; urgency=low

  * **Initial Natty kernel version and ABI (2.6.36-0)**
  * drop last vestiges of lpia architecture
  * disable linux-backports-modules
  * drop omap for armel

[https://lists.ubuntu.com/archives/natty-changes/2010-October/000295.html](https://lists.ubuntu.com/archives/natty-changes/2010-October/000295.html)


Works just fine....

---

### Post by cariboo on 2010-10-18
I've been using it for a couple of hours, everything seems to be running ok.

---

### Post by Starks on 2010-10-18
> **plun said:**
> Today we have Nattys first 2.6.36 kernel....



Works just fine....
The first four kernels have been available for a week in the repos.

[https://launchpad.net/ubuntu/+source/linux/2.6.36-0.4](https://launchpad.net/ubuntu/+source/linux/2.6.36-0.4)

---

### Post by DougieFresh4U on 2010-10-18
> **plun said:**
> Today we have Nattys first 2.6.36 kernel....



Works just fine....

Do I dare ask, but I have been using the 2.6.36rc8 kernel. Help me understand, which is the 'newest' kernel version? Grub will list rc8 at the top. I am on my Windows7 at the moment so I can't show what I mean with grub menu.
I would appreciate any one who can clear this up for me.

---

### Post by McTwitch on 2010-11-03
Up and running! Two updates and upgrades, no breaks yet.

---

### Post by wilee-nilee on 2010-11-04
Have it in Vbox for now.

---

### Post by ancleessen4 on 2010-11-04
Running in VirtualBox-standing by for action :biggrin:

---

### Post by susema on 2010-11-09
I'm up, too..

> susema@susema:~$ uname -r2.6.37-2-generic
susema@susema:~$ cat /etc/lsb-releaseDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

---

### Post by Wobblybob on 2010-11-13
Having now built a PC from the bits I have lying around for Testing this release, I'm now up;

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

```

Testing PC;
AMD Athlon XP 2000+
2GB RAM
nVidia NV34 GeForce FX5200 with 512 MB on board.
ASRock K7S41Gx Motherboard with SiS 741Gx chipset
120 GB HD

---

### Post by matt_symes on 2010-11-13
Hi

Well mine got hosed today after a failed update. Shame. Its a problem in  gnome. No panels or cairo dock and such like. 

Still responds to input though. Can  start applications with alt + F2  Will look in the logs tomorrow. See what they show.

Back on 10.04 for the moment.

Kind regards

---

### Post by zika on 2010-11-14
Did You try [http://ubuntuforums.org/showpost.php?p=10110366&postcount=10](http://ubuntuforums.org/showpost.php?p=10110366&postcount=10) ...?

---

### Post by matt_symes on 2010-11-14
Hi

__zika. Thankyou!! Had not read that.

Kind regards

---

### Post by zika on 2010-11-14
> **matt_symes said:**
> Hi

__zika. Thankyou!! Had not read that.

Kind regards
All credits go to chrisccoulson, I was just a messenger... :)

---

### Post by matt_symes on 2010-11-14
Hi

> All credits go to chrisccoulson, I was just a messenger... :smile:

Then i thank you all :)

Kind regards

---

### Post by PGHammer on 2010-11-20
> **Spice Weasel said:**
> You crazy, crazy people.

Still, this does sound fun. *wants to try*

That's what VMs are for (I'm doing two Natty VMs - one each for Ubuntu and Kubuntu).

---

### Post by McTwitch on 2010-11-25
Updated today, went alright. But then I tried to upgrade, and got met with this

```
jeremy@Jer:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apport-gtk bind9-host compiz compiz-core compiz-fusion-plugins-main
  compiz-gnome compiz-plugins cpu-checker dhcp3-client dhcp3-common dnsutils
  dvd+rw-tools evolution-plugins gnome-applets gnome-applets-data gnome-panel
  gnome-panel-data iptables kmess libbind9-60 libcanberra-gtk0
  libcompizconfig0 libisccc60 liblaunchpad-integration1 liblwres60 libnm-glib2
  libnm-util1 linux-generic linux-headers-generic linux-image-generic man-db
  mousetweaks network-manager ubuntu-minimal update-manager
  update-manager-core vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.

```

I tried upgrading each individually as well, only to be met with the same result. What's wrong?

---

### Post by cariboo on 2010-11-25
I would suggest you open up synaptic, and see what is holding the update back, it may be a dependency not met, or missing packages.

---

### Post by susema on 2010-11-25
> **McTwitch said:**
> Updated today, went alright. But then I tried to upgrade, and got met with this
I tried upgrading each individually as well, only to be met with the same result. What's wrong?

Try this;

```
sudo apt-get install aptitude && sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by McTwitch on 2010-11-25
Thanks. The two suggestions, along with --fix-missing seems to have gotten most upgraded. There are still seven that I'm not upgrading.

---

