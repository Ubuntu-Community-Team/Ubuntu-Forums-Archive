---
title: "apt-get recommend should be reverted."
date: 2010-05-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by LKjell on 2010-05-13
By default now everything in recommended is installed this sort of annoy me a lot. I justed install one kde package and it pull in the whole kde desktop. Everything get clutted up and bloated with useless program I will never use.

The fix now is to have **APT::Install-Recommends "false";** in /etc/apt/apt.conf Or that package maintainer keep the recommend field to just programs that *is* recommended...

If you want to see what I mean then have a clean Ubuntu install and install kigo and see what else you get with you.

---

### Post by wojox on 2010-05-13
Wow your not kidding

```

wojox@wojox-desktop:~$ sudo aptitude install kigo
[sudo] password for wojox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  akonadi-server{a} exiv2{a} gdebi-kde{a} gnugo{a} icoutils{a} install-package{a} kdebase-runtime{a} 
  kdebase-runtime-data{a} kdebase-workspace-bin{a} kdebase-workspace-data{a} 
  kdebase-workspace-kgreet-plugins{a} kdelibs-bin{a} kdelibs5{a} kdelibs5-data{a} kdepim-runtime{a} 
  kdepimlibs-data{a} kdepimlibs5{a} kdesudo{a} kigo kpackagekit{a} ksysguardd{a} kubuntu-debug-installer{a} 
  libakonadiprivate1{a} libattica0{a} libaudio2{a} libboost-program-options1.40.0{a} libclucene0ldbl{a} 
  libdbusmenu-qt2{a} libexiv2-6{a} libiodbc2{a} libkdegames5{a} libkephal4{a} libkfontinst4{a} 
  libkscreensaver5{a} libksgrd4{a} libkworkspace4{a} libmng1{a} libmysqlclient16{a} libpackagekit-glib2-12{a} 
  libpackagekit-qt-12{a} libphonon4{a} libplasma-applet-system-monitor4{a} libplasma-geolocation-interface4{a} 
  libplasma3{a} libplasmaclock4{a} libplasmagenericshell4{a} libpolkit-qt-1-0{a} libprocesscore4{a} 
  libprocessui4{a} libqca2{a} libqimageblitz4{a} libqt4-assistant{a} libqt4-dbus{a} libqt4-designer{a} 
  libqt4-help{a} libqt4-network{a} libqt4-opengl{a} libqt4-qt3support{a} libqt4-script{a} 
  libqt4-scripttools{a} libqt4-sql{a} libqt4-sql-mysql{a} libqt4-svg{a} libqt4-test{a} libqt4-webkit{a} 
  libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtgui4{a} libsolidcontrol4{a} libsolidcontrolifaces4{a} 
  libsoprano4{a} libssh-4{a} libstreamanalyzer0{a} libstreams0{a} libtaskmanager4{a} libweather-ion4{a} 
  libxcb-shape0{a} libxcb-shm0{a} libxcb-xv0{a} libxine1{a} libxine1-bin{a} libxine1-console{a} 
  libxine1-misc-plugins{a} libxine1-x{a} mysql-client-core-5.1{a} mysql-common{a} mysql-server-core-5.1{a} 
  oxygen-icon-theme{a} packagekit{a} packagekit-backend-apt{a} phonon{a} phonon-backend-xine{a} 
  plasma-dataengines-workspace{a} plasma-scriptengine-javascript{a} plasma-widgets-workspace{a} 
  polkit-kde-1{a} python-kde4{a} python-packagekit{a} python-qt4{a} python-sip{a} shared-desktop-ontologies{a} 
  software-properties-kde{a} soprano-daemon{a} ttf-dejavu{a} ttf-dejavu-extra{a} update-manager-kde{a} 
  virtuoso-nepomuk{a} 
0 packages upgraded, 108 newly installed, 0 to remove and 0 not upgraded.
Need to get 101MB of archives. After unpacking 337MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

---

### Post by ronacc on 2010-05-13
you can do the same thing using synaptic .  Settings>preferences>uncheck consider recommends as dependencies  .

---

### Post by Longinus00 on 2010-05-13
> **LKjell said:**
> By default now everything in recommended is installed this sort of annoy me a lot. I justed install one kde package and it pull in the whole kde desktop. Everything get clutted up and bloated with useless program I will never use.

The fix now is to have **APT::Install-Recommends "false";** in /etc/apt/apt.conf Or that package maintainer keep the recommend field to just programs that *is* recommended...

If you want to see what I mean then have a clean Ubuntu install and install kigo and see what else you get with you.

You realize kigo is a kde app so will of course pull in all its kde dependencies right? Try installing gtk apps in kde and you'll see the same thing (in reverse).

[http://packages.ubuntu.com/lucid/kigo](http://packages.ubuntu.com/lucid/kigo)

I'm also pretty sure the change was first made in debian.

---

### Post by ibuclaw on 2010-05-13
> **wojox said:**
> Wow your not kidding


Aptitude installing recommends has always been the default behaviour.

Apt-get must have been introduced this recently (this seems to be the case in Lucid too).

---

### Post by xebian on 2010-05-13
> **LKjell said:**
> By default now everything in recommended is installed this sort of annoy me a lot. I justed install one kde package and it pull in the whole kde desktop. Everything get clutted up and bloated with useless program I will never use.

The fix now is to have **APT::Install-Recommends "false";** in /etc/apt/apt.conf Or that package maintainer keep the recommend field to just programs that *is* recommended...

If you want to see what I mean then have a clean Ubuntu install and install kigo and see what else you get with you.

If that's what you want then by all means turn it off.  Just because you want it off doesn't mean everyone else should have it.

It's not broken so there's nothing to fix.

---

### Post by LKjell on 2010-05-14
> **Longinus00 said:**
> You realize kigo is a kde app so will of course pull in all its kde dependencies right? Try installing gtk apps in kde and you'll see the same thing (in reverse).

[http://packages.ubuntu.com/lucid/kigo](http://packages.ubuntu.com/lucid/kigo)

I'm also pretty sure the change was first made in debian.

Which is a problem because you do not need system apps from "the other side" you just need the runtime.

> **xebian said:**
> If that's what you want then by all means turn it off.  Just because you want it off doesn't mean everyone else should have it.

It's not broken so there's nothing to fix.

It was off before so by you logic it should be off. So if you want it on then you turn it on.

I can see that the recommend field is useful but some package maintainer misuse it and put a lot of crap in it. We have meta packages to pull in.

A lot of people want delta deb, but if they look at this they would realize this takes a lot of bandwidth.

---

### Post by dino99 on 2010-05-14
the result on my system : huge difference  :mad:

the number of files and folders installed have jumped to > 252000 now, was 120000 previously  :P

---

### Post by plun on 2010-05-14
> **dino99 said:**
> the result on my system : huge difference  :mad:

the number of files and folders installed have jumped to > 252000 now, was 120000 previously  :P

Time for a "Pure Gnome" cleaning....:)

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

;)

---

### Post by dino99 on 2010-05-14
> **plun said:**
> Time for a "Pure Gnome" cleaning....:)

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

;)

Thanks, i was commenting about Maverick, but still searching a script or something to find all the oldies left behind ( i've upgraded the sources.list)

---

### Post by plun on 2010-05-14
> **dino99 said:**
> Thanks, i was commenting about Maverick, but still searching a script or something to find all the oldies left behind ( i've upgraded the sources.list)

The kubuntu-desktop meta package isn't changed for Maverick so Psychocats Kubuntu removal can be used.

---

### Post by dino99 on 2010-05-14
> **plun said:**
> The kubuntu-desktop meta package isn't changed for Maverick so Psychocats Kubuntu removal can be used.

looking the repo into synaptic, there is no kubuntu or xubuntu packages installed, as these packages are in the cache, i think the installer is faulty about the packages number installed. I've already seen it jumping down or up without easy explanations with lucid too.

---

### Post by VeeDubb on 2010-05-14
The problem with turning off recommends is that it makes life very difficult for the average user.

For instance, a lot of things that really should be 'depends' are listed as recommended.  When you install something like battle for wesnoth without installing the recommended packages, you get no sound, and only half the maps.

If you were going to do away with recommends, you'd either need the package maintainers to do some serious reevaluation of what should be a dependency, or you'd need to make changes to apt that allowed for 3 levels of dependency; dependes, strongly recommended, and recommended.  Of course, that just opens up a whole whole new can of worms.

---

### Post by dino99 on 2010-05-14
> **VeeDubb said:**
> The problem with turning on recommends is that it makes life very difficult for the average user.

For instance, a lot of things that really should be 'depends' are listed as recommended.  When you install something like battle for wesnoth without installing the recommended packages, you get no sound, and only half the maps.

If you were going to do away with recommends, you'd either need the package maintainers to do some serious reevaluation of what should be a dependency, or you'd need to make changes to apt that allowed for 3 levels of dependency; dependes, strongly recommended, and recommended.  Of course, that just opens up a whole whole new can of worms.

i've reported several times about this lack of misconfiguration as some maintainers does well and others dont mind

---

### Post by LKjell on 2010-05-14
> **VeeDubb said:**
> The problem with turning on recommends is that it makes life very difficult for the average user.

For instance, a lot of things that really should be 'depends' are listed as recommended.  When you install something like battle for wesnoth without installing the recommended packages, you get no sound, and only half the maps.

If you were going to do away with recommends, you'd either need the package maintainers to do some serious reevaluation of what should be a dependency, or you'd need to make changes to apt that allowed for 3 levels of dependency; dependes, strongly recommended, and recommended.  Of course, that just opens up a whole whole new can of worms.

Well you do have meta packages that says minimum, default, or full.
And packages that is consider to make up a full entity should depend on each other. But then as you can see here kigo is not the kde desktop. Or for instance if I had kubuntu and wanted to try out gedit I do not want to install the whole ubuntu-desktop.

Then there are some packages I just wish the recommend to work. Texlive is for instance. I want those extra packages to be installed but it does not do that by default.

---

### Post by VeeDubb on 2010-05-14
> **dino99 said:**
> i've reported several times about this lack of misconfiguration as some maintainers does well and others dont mind

> **LKjell said:**
> Well you do have meta packages that says minimum, default, or full.

I guess it really comes down to the package maintainers.  There are some great ones out there that put together good/clear metapackages, and do a great job of using their brains when listing dependencies vs recommended packages, but I think that for the majority of users, it's still easier to have recommended packages installed by default.

Perhaps another way to handle it would be to have recommended packages turned off by default in synaptic and command line apt/aptitude, but keep it enabled in the Software Center.

---

### Post by dino99 on 2010-05-14
> **VeeDubb said:**
> I guess it really comes down to the package maintainers.  There are some great ones out there that put together good/clear metapackages, and do a great job of using their brains when listing dependencies vs recommended packages, but I think that for the majority of users, it's still easier to have recommended packages installed by default.

Perhaps another way to handle it would be to have recommended packages turned off by default in synaptic and command line apt/aptitude, but keep it enabled in the Software Center.

i dream about a light system that really work to find a missed package when needed and dynamically activate/desactivate services on the fly. I know that ubuntu already have that feature, i only wait it to work smootly, and in most of the case it fail or even dont try at all.

---

### Post by MacUntu on 2010-05-14
> **LKjell said:**
> It was off before

> Recommended packages installed by default

In accordance with the Debian Policy Manual (which says "The 'Recommends' field should list packages that would be found together with this one in all but unusual installations"), the package management system now installs packages listed in the Recommends: field of other installed packages as well as Depends: by default. If you want to avoid this for specific packages, use apt-get --no-install-recommends; if you want to make this permanent, set APT::Install-Recommends "false"; in /etc/apt/apt.conf. Be aware that this may result in missing features in some programs. 

(**This change was made in Ubuntu 8.10.**)

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by ibuclaw on 2010-05-14
> **MacUntu said:**
> [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Perhaps they are getting too lenient on their Recommended packages then. As it is IMO getting a bit too much.

Though, to do the opposite, and turn off recommends can be even worse and result in unusable applications.

ie:
```
sudo apt-get install quickly --no-install-recommends
```
Installs the core applications, but nothing that you require to get setup in anything. ie: This doesn't work because there is no command for 'create'
```
quickly create ubuntu-application foobar
```

A little better thought into what is a recommend and what is a dependency needs a little tweak in it's specification /me thinks. ;)

---

### Post by ronacc on 2010-05-14
And I complained about it back then too . depends should mean depends , not " someone might possibly find a use for this someday " .

---

### Post by LKjell on 2010-05-14
MacUntu, I do not know your intention with that quote. But yes the change was made in 8.10 so it means it was not there in 8.04 which just happen to be a LTS. We usually do not care what happen during the normal releases. What really changing is from a LTS to another LTS.

As the policy manual state the recommend should be packages which group together as a program. But Kigo and update-manage-kde has no relation except that they are kde programs.

---

### Post by MacUntu on 2010-05-14
> **LKjell said:**
> We usually do not care what happen during the normal releases.

If you are *that* concerned maybe you should? ;)

> **LKjell said:**
> But Kigo and update-manage-kde has no relation except that they are kde programs.

Sounds more like a bug than an issue with that setting.

---

### Post by Yofel on 2010-05-14
> **LKjell said:**
>  But Kigo and update-manage-kde has no relation except that they are kde programs.

That's not a bug but an unlucky case of recursive depends/recommends:

kigo depends on kdebase-runtime, which recommends kubuntu-debug-installer, which depends on kpackagekit, which depends on update-manager-kde.

---

### Post by glasen on 2010-05-14
> **ibuclaw said:**
> Though, to do the opposite, and turn off recommends can be even worse and result in unusable applications.

If an application needs a package to be usable, this package must be a "required" dependency not a "recommended" one. Otherwise the package is broken. You cannot demand every user to activate the "install all recommends"-flag for your package.

"Recommends" should only be used if a package adds additional functionality which is not necessarily needed.

---

### Post by dino99 on 2010-05-14
> **Yofel said:**
> That's not a bug but an unlucky case of recursive depends/recommends:

kigo depends on kdebase-runtime, which recommends kubuntu-debug-installer, which depends on kpackagekit, which depends on update-manager-kde.

that way , at the end, the entire repo is installed :mad: Looking at some packages, their "recommends" packages are so numerous, and cant understand why, push the distro into a real mess. Really need an exact "recommend" list for each package.

see post # 8

---

### Post by LKjell on 2010-05-14
> **glasen said:**
> 
...
"Recommends" should only be used if a package adds additional functionality which is not necessarily needed.

In the case of Wesnoth where sound is optional should it be pulled in or not?

---

### Post by Longinus00 on 2010-05-14
If you're **really** anal about what packages get installed then there's always slackware or gentoo. As it stands, changing the behavior with regards to 'recommends' is just going to break a bunch of things and confuse users who want to install a package and have it be useful right away without having to search through dependency lists. If you're still mad go bring it up with the debian guys, see how well that goes.

---

### Post by glasen on 2010-05-14
> **LKjell said:**
> In the case of Wesnoth where sound is optional should it be pulled in or not?

In case of this game, the music-package is not required. It's not necessarily needed to play the game. You can play the game without music.

P.S.: The music of Wesnoth does get on my nerves after one or two missions. It's always the same track for every mission in a scenario. Therefore i don't even install the music-package and listen to my own music (radio or MP3-files) in Rhythmbox.

> **Longinus00 said:**
> As it stands, changing the behavior with regards to 'recommends' is just going to break a bunch of things and confuse users who want to install a package and have it be useful right away without having to search through dependency lists.

As i wrote above, if an application does not work without a recommended package, than the application-package is broken.

"Recommends" means you can install the package, but you haven't or are not forced to install it.

> **Longinus00 said:**
> If you're still mad go bring it up with the debian guys, see how well that goes.

Why discuss with the Debian guys? If the Ubuntu-devs decide to change the default setting to not install recommended packages, it's their decision. Ubuntu is based on Debian, but it is not Debian!

---

### Post by Longinus00 on 2010-05-14
> **glasen said:**
> 
As i wrote above, if an application does not work without a recommended package, than the application-package is broken.

"Recommends" means you can install the package, but you haven't or are not forced to install it.

I never said that. I said recommended packages made the application useful.

> **glasen said:**
> 
Why discuss with the Debian guys? If the Ubuntu-devs decide to change the default setting to not install recommended packages, it's their decision. Ubuntu is based on Debian, but it is not Debian!

You know all those debs you can install via universe? Who made those packages? Who maintains those packages?

---

### Post by 23meg on 2010-05-14
> **glasen said:**
> 
"Recommends" should only be used if a package adds additional functionality which is not necessarily needed.

> **glasen said:**
> 
"Recommends" means you can install the package, but you haven't or are not forced to install it.

The above statements are not true according to the Debian Policy Manual, which is the definitive document for this subject, and which defines the "Recommends" field as follows:

> **Recommends**

This declares a strong, but not absolute, dependency.

The Recommends field should list packages that would be found together with this one in all but unusual installations.

Your and some others' definition of "Recommends" is perhaps closer to the dictionary definition of the word, but it's the policy that matters. But then it's also close to the dictionary definition of the words "suggest" and "enhance", and the DPM's definitions of the already existing "Suggests" and "Enhances" fields:

> **Suggests**

    This is used to declare that one package may be more useful with one or more others. Using this field tells the packaging system and the user that the listed packages are related to this one and can perhaps enhance its usefulness, but that installing this one without them is perfectly reasonable.

**Enhances**

    This field is similar to Suggests but works in the opposite direction. It is used to declare that a package can enhance the functionality of another package.


> **glasen said:**
> Why discuss with the Debian guys? If the Ubuntu-devs decide to change the default setting to not install recommended packages, it's their decision. Ubuntu is based on Debian, but it is not Debian!

Changing fundamental behaviors of package managers arbitrarily without regard to what our most important upstream does would not be a good idea, especially given that we intensively merge/sync packages with Debian, and we make little or no modifications to the majority of Debian packages by number, which means that the DPM pretty much directly applies to most of Ubuntu (the Ubuntu Policy Manual is derived from it, with a few modifications, and changes to the DPM are reflected in it).

---

### Post by VeeDubb on 2010-05-14
> **23meg said:**
> Your and some others' definition of "Recommends" is perhaps closer to the dictionary definition of the word, but it's the policy that matters.

The problem still comes back to the package maintainers.  Many of them clearly use recommends as laid out in the policy, while other put all sorts of stuff in the recommends field that *barely* even meets the "dictionary definition" as you put it.

I've always said, it really doesn't matter what the rules are, as long as everybody is using the same rule.  Unfortunately, there are package maintainers that list plenty of things that should go in enhance, or in some cases have only some tangential connection and add no real functionality, as recommends.

---

### Post by 23meg on 2010-05-14
> **VeeDubb said:**
> The problem still comes back to the package maintainers.  Many of them clearly use recommends as laid out in the policy, while other put all sorts of stuff in the recommends field that *barely* even meets the "dictionary definition" as you put it.

I've always said, it really doesn't matter what the rules are, as long as everybody is using the same rule.  Unfortunately, there are package maintainers that list plenty of things that should go in enhance, or in some cases have only some tangential connection and add no real functionality, as recommends.

If that's the case, the way to fix that is to file bug reports in packages that do not use "Recommends" properly, preferably in Debian, citing the DPM definition of the field; not violating the DPM entirely just because some package(r)s don't obey it.

---

### Post by seeker5528 on 2010-05-14
> **dino99 said:**
> that way , at the end, the entire repo is installed :mad: Looking at some packages, their "recommends" packages are so numerous, and cant understand why, push the distro into a real mess. Really need an exact "recommend" list for each package.

Are you sure you are looking at a list that is just the recommends? 

In Synaptic for example, if you right click a package so you can select software that is recommended, so if something recommends 'web browser' any package indicating that it provides 'web browser' will be shown. If you look at the package properties, then you see the actual depends and recommends lists.

People that know this stuff can change the default for how to treat recommends, for people that don't know it's better to treat the recommends as dependencies. If people don't know, but want to know what's going on, they can be educated.

If you think it's too excessive you can file a bug.

If you are installing a KDE app in Gnome or Gnome app in KDE, and it's the first time, you can expect to have to install a chunk of stuff. If it's a QT app in Gnome or GTK app in KDE, then you expect less stuff to be pulled in.

Later, Seeker

---

### Post by glasen on 2010-05-14
> **23meg said:**
> If that's the case, the way to fix that is to file bug reports in packages that do not use "Recommends" properly, preferably in Debian, citing the DPM definition of the field; not violating the DPM entirely just because some package(r)s don't obey it.

This would be definitely the best solution for this problem.

---

### Post by VeeDubb on 2010-05-14
> **23meg said:**
> If that's the case, the way to fix that is to file bug reports in packages that do not use "Recommends" properly, preferably in Debian, citing the DPM definition of the field; not violating the DPM entirely just because some package(r)s don't obey it.

I really can't argue with that one.  Works for me.

---

### Post by LKjell on 2010-05-15
> **glasen said:**
> This would be definitely the best solution for this problem.

Best is not the easiest. Consider the amount of packages that have this problem. I rather have an announcement that next time they pack a package take a check in the recommend field and see if it can be trimmed down.

---

### Post by glasen on 2010-05-15
> Best is not the easiest. Consider the amount of packages that have this problem. 

This is true. But otherwise it could very easy:

Just write an email to every maintainer of a package you are using on a daily basis and ask if the package dependencies could revised.

---

### Post by xebian on 2010-05-15
> **23meg said:**
> If that's the case, the way to fix that is to file bug reports in packages that do not use "Recommends" properly, preferably in Debian, citing the DPM definition of the field; not violating the DPM entirely just because some package(r)s don't obey it.

Or better still Ubuntu should build their own packages instead of blaming Debian.

---

### Post by 23meg on 2010-05-15
> **xebian said:**
> Or better still Ubuntu should build their own packages instead of blaming Debian.

Blaming Debian? Who's doing that? We're simply complying with Debian policy.

---

### Post by xebian on 2010-05-15
> **23meg said:**
> Blaming Debian? Who's doing that? We're simply complying with Debian policy.

That's besides the point.  Compliant or not, for taking a Debian package and distributing it as an Ubuntu package is your responsibility.  Don't be telling Ubuntu users to go complain at Debian when Ubuntu knowing of the flaws should build/rebuild it to Ubuntu's policy.

---

### Post by seeker5528 on 2010-05-15
> **xebian said:**
> Or better still Ubuntu should build their own packages instead of blaming Debian.

Is there a better example where it is shown that the recommends field is abused?

Looking at the first post > **LKjell said:**
> If you want to see what I mean then have a clean Ubuntu install and install kigo and see what else you get with you. and seeing the result of that in the second > **wojox said:**
> Wow your not kidding

```

wojox@wojox-desktop:~$ sudo aptitude install kigo
[sudo] password for wojox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  akonadi-server{a} exiv2{a} gdebi-kde{a} gnugo{a} icoutils{a} install-package{a} kdebase-runtime{a} 
  kdebase-runtime-data{a} kdebase-workspace-bin{a} kdebase-workspace-data{a} 
  kdebase-workspace-kgreet-plugins{a} kdelibs-bin{a} kdelibs5{a} kdelibs5-data{a} kdepim-runtime{a} 
  kdepimlibs-data{a} kdepimlibs5{a} kdesudo{a} kigo kpackagekit{a} ksysguardd{a} kubuntu-debug-installer{a} 
  libakonadiprivate1{a} libattica0{a} libaudio2{a} libboost-program-options1.40.0{a} libclucene0ldbl{a} 
  libdbusmenu-qt2{a} libexiv2-6{a} libiodbc2{a} libkdegames5{a} libkephal4{a} libkfontinst4{a} 
  libkscreensaver5{a} libksgrd4{a} libkworkspace4{a} libmng1{a} libmysqlclient16{a} libpackagekit-glib2-12{a} 
  libpackagekit-qt-12{a} libphonon4{a} libplasma-applet-system-monitor4{a} libplasma-geolocation-interface4{a} 
  libplasma3{a} libplasmaclock4{a} libplasmagenericshell4{a} libpolkit-qt-1-0{a} libprocesscore4{a} 
  libprocessui4{a} libqca2{a} libqimageblitz4{a} libqt4-assistant{a} libqt4-dbus{a} libqt4-designer{a} 
  libqt4-help{a} libqt4-network{a} libqt4-opengl{a} libqt4-qt3support{a} libqt4-script{a} 
  libqt4-scripttools{a} libqt4-sql{a} libqt4-sql-mysql{a} libqt4-svg{a} libqt4-test{a} libqt4-webkit{a} 
  libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtgui4{a} libsolidcontrol4{a} libsolidcontrolifaces4{a} 
  libsoprano4{a} libssh-4{a} libstreamanalyzer0{a} libstreams0{a} libtaskmanager4{a} libweather-ion4{a} 
  libxcb-shape0{a} libxcb-shm0{a} libxcb-xv0{a} libxine1{a} libxine1-bin{a} libxine1-console{a} 
  libxine1-misc-plugins{a} libxine1-x{a} mysql-client-core-5.1{a} mysql-common{a} mysql-server-core-5.1{a} 
  oxygen-icon-theme{a} packagekit{a} packagekit-backend-apt{a} phonon{a} phonon-backend-xine{a} 
  plasma-dataengines-workspace{a} plasma-scriptengine-javascript{a} plasma-widgets-workspace{a} 
  polkit-kde-1{a} python-kde4{a} python-packagekit{a} python-qt4{a} python-sip{a} shared-desktop-ontologies{a} 
  software-properties-kde{a} soprano-daemon{a} ttf-dejavu{a} ttf-dejavu-extra{a} update-manager-kde{a} 
  virtuoso-nepomuk{a} 
0 packages upgraded, 108 newly installed, 0 to remove and 0 not upgraded.
Need to get 101MB of archives. After unpacking 337MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

Yes it is a big chunk of stuff. No it is not all necessary. It is not the entire KDE desktop by far even for what you would consider a basic KDE desktop installation and by the time you factor in QT, KDE base, KDE workspace, Plasma, the help system and crash handling, and what they require, there is not really that much extra.

Personally, I think it would be a stretch to say it violates what was listed as policy in this quote from earlier in the thread > **MacUntu said:**
> > 
Recommended packages installed by default

In accordance with the Debian Policy Manual (which says "The 'Recommends' field should list packages that would be found together with this one in all but unusual installations"), the package management system now installs packages listed in the Recommends: field of other installed packages as well as Depends: by default. If you want to avoid this for specific packages, use apt-get --no-install-recommends; if you want to make this permanent, set APT::Install-Recommends "false"; in /etc/apt/apt.conf. Be aware that this may result in missing features in some programs.

(This change was made in Ubuntu 8.10.) 

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

EDIT: It should probably be noted that the Kigo example was not intended to show there was abuse, because that claim had not been made yet.

Later, Seeker

---

### Post by 23meg on 2010-05-15
> **xebian said:**
> That's besides the point.  Compliant or not, for taking a Debian package and distributing it as an Ubuntu package is your responsibility.  Don't be telling Ubuntu users to go complain at Debian when Ubuntu knowing of the flaws should build/rebuild it to Ubuntu's policy.

Not diverging from Debian's fundamental policies unless absolutely needed, and keeping as small a delta as possible with Debian have been principles of Ubuntu development from the beginning. They're advantageous to both sides, and violating them at will without thoroughly looking into other ways of fixing issues that arise is not going to be. In this case, there's no compelling reason why Ubuntu should *not* install recommended packages automatically, when Debian *does*. If it's a problem, it's a problem for both sides. If it's good, it's good for both.

Besides, Ubuntu users are welcome to report packaging bugs including incorrect use of fields such as "Recommends" in the Ubuntu bug tracker, and such bugs would be forwarded to the Debian BTS, and/or fixed directly in Debian if the maintainer is common or someone is interested in getting a fix in; however, it's extra work for all involved, and reporting common issues in Debian ensures that Debian benefits from the fix as well. It wouldn't be a stretch to assume that most people who care enough to worry about details such as these already know or can figure out how to report a bug in Debian.

---

### Post by ssam on 2010-05-16
i am pretty sure the main reason for this change was to make possible to remove things like evolution without removing ubuntu-desktop. it also has the advantage that when you install a program all of its features work.

in the days before ubuntu-desktop DEPENDed on evolution. now ubuntu-desktop only RECOMMENDs evolution.

if you want less things to be installed you could ask that packages move things from RECOMMEND to SUGGESTS.

---

### Post by Reiger on 2010-05-16
Yes recommends -> suggests; although if you are a KDE user and stick to KDE packages, or a gnome user and stick to GNOME ones things are not actually that bad. Or alternatively use the -R flag of aptitude judiciously (including during safe-upgrade).

---

### Post by 23meg on 2010-05-16
> **ssam said:**
> i am pretty sure the main reason for this change was to make possible to remove things like evolution without removing ubuntu-desktop. it also has the advantage that when you install a program all of its features work.

in the days before ubuntu-desktop DEPENDed on evolution. now ubuntu-desktop only RECOMMENDs evolution.

That was achieved by implementing "Recommends" support in APT (yes; despite Debian policy, not all frontends to dpkg supported it), and modifying the default metapackages to use "Recommends" instead of "Depends", back in Ubuntu 7.04. Installing recommended packages by default in all cases came later in Ubuntu 8.10, due to problems the change caused with release upgrade cases.

---

### Post by dino99 on 2010-05-16
> **23meg said:**
> That was achieved by implementing "Recommends" support in APT (yes; despite Debian policy, not all frontends to dpkg supported it), and modifying the default metapackages to use "Recommends" instead of "Depends", back in Ubuntu 7.04. Installing recommended packages by default in all cases came later in Ubuntu 8.04, due to problems the change caused with release upgrade cases.

i'm looking at the package which count the database when we apply upgrades: opening the details box when upgrading, i see now that counter saying about 230000 packages installed, was about 150000 with lucid and 120000 before. Thats seems way to much, and cant trust this so huge number, dont know about which package to report.

---

### Post by LKjell on 2010-05-16
> **seeker5528 said:**
> Is there a better example where it is shown that the recommends field is abused?

Looking at the first post  and seeing the result of that in the second 

Yes it is a big chunk of stuff. No it is not all necessary. It is not the entire KDE desktop by far even for what you would consider a basic KDE desktop installation and by the time you factor in QT, KDE base, KDE workspace, Plasma, the help system and crash handling, and what they require, there is not really that much extra.

Personally, I think it would be a stretch to say it violates what was listed as policy in this quote from earlier in the thread 

EDIT: It should probably be noted that the Kigo example was not intended to show there was abuse, because that claim had not been made yet.

Later, Seeker

By the fact that some programs in there you do not need at all on a gnome system is what I call abusing.

With recommend field you can end with two packages that depends on each other in a circular way. It also means that there is a potential that some package can depends on those big meta packages. And you then end with a system that you really do not want.

---

### Post by ranch hand on 2010-05-16
There is a cure for that.  Netboot install, Gnome desktop instead of Ubuntu desktop and most of that stuff is gone.

---

### Post by ibuclaw on 2010-05-16
> **dino99 said:**
> i'm looking at the package which count the database when we apply upgrades: opening the details box when upgrading, i see now that counter saying about 230000 packages installed, was about 150000 with lucid and 120000 before. Thats seems way to much, and cant trust this so huge number, dont know about which package to report.

230,000 .... don't you mean 2,300 ? (I mean ... there are only circa 30,000 packages available across all default ubuntu repositories...).

---

### Post by MacUntu on 2010-05-16
Fresh Lucid -> Maverick upgrade shows 1300 installed packages.

---

### Post by LKjell on 2010-05-17
> **MacUntu said:**
> Fresh Lucid -> Maverick upgrade shows 1300 installed packages.

That is not fun. Try hardy up to lucid without taking the shortcut and check what crap you might also get.

---

### Post by dino99 on 2010-05-17
> **ibuclaw said:**
> 230,000 .... don't you mean 2,300 ? (I mean ... there are only circa 30,000 packages available across all default ubuntu repositories...).

yeah these counts are way too high, and this counter is crazy for sure and need to report against, but what is the package: apt, dpkg, else ?

---

### Post by MacUntu on 2010-05-17
Where do you see that counter?

> **LKjell said:**
> That is not fun. Try hardy up to lucid without taking the shortcut and check what crap you might also get.

I was just responding to those 230,000/2,300. ;)

---

### Post by psusi on 2010-05-17
No, recommends by default has been on for quite some time, as far back as 8.04 I think, and is not going away.  Recommends is supposed to be used when the packages are not strictly required to operate at all, but are needed to provide the functionality most users EXPECT when they install the package.  It sounds like you have found a particular package that is recommending far more than it should, so you should file a bug against that package.

---

### Post by MacUntu on 2010-05-17
> **LKjell said:**
> Try hardy up to lucid

Holy sh*t, Batman!

Out of curiosity I did exactly that: installed Hardy and upgraded to Intrepid, Jaunty, Karmic, Lucid, and Maverick:

[LIST][*]Hardy install, fully updated: 1100 packages, 2.3 GB
[*]Upgrade to Intrepid: 1150 packages, 2.4 GB
[*]Upgrade to Jaunty: 1300 packages, 2.3 GB
[*]Upgrade to Karmic: 1500 packages, 2.9 GB
[*]Upgrade to Lucid: 1600 packages, 3.2 GB
[*]Upgrade to Maverick: **1600 packages, 3.3 GB**[/LIST]
vs.

[LIST][*]Maverick upgrade from updated Lucid install: **1300 packages, 2.3 GB**[/LIST]

That's a difference of one GB and 300 packages! I did expect differences but not to this extent. So much for upgrade vs. fresh install. :KS

---

### Post by taavikko on 2010-05-17
> **MacUntu said:**
> Holy sh*t, Batman!

Out of curiosity I did exactly that: installed Hardy and upgraded to Intrepid, Jaunty, Karmic, Lucid, and Maverick:

[LIST][*]Hardy install, fully updated: 1100 packages, 2.3 GB
[*]Upgrade to Intrepid: 1150 packages, 2.4 GB
[*]Upgrade to Jaunty: 1300 packages, 2.3 GB
[*]Upgrade to Karmic: 1500 packages, 2.9 GB
[*]Upgrade to Lucid: 1600 packages, 3.2 GB
[*]Upgrade to Maverick: **1600 packages, 3.3 GB**[/LIST]
vs.

[LIST][*]Maverick upgrade from updated Lucid install: **1300 packages, 2.3 GB**[/LIST]

That's a difference of one GB and 300 packages! I did expect differences but not to this extent. So much for upgrade vs. fresh install. :KS

Out of curiosity, did ex. aptitude show obsolete packages?

---

### Post by Arla on 2010-05-17
> **MacUntu said:**
> Holy sh*t, Batman!

Out of curiosity I did exactly that: installed Hardy and upgraded to Intrepid, Jaunty, Karmic, Lucid, and Maverick:

[LIST][*]Hardy install, fully updated: 1100 packages, 2.3 GB
[*]Upgrade to Intrepid: 1150 packages, 2.4 GB
[*]Upgrade to Jaunty: 1300 packages, 2.3 GB
[*]Upgrade to Karmic: 1500 packages, 2.9 GB
[*]Upgrade to Lucid: 1600 packages, 3.2 GB
[*]Upgrade to Maverick: **1600 packages, 3.3 GB**[/LIST]
vs.

[LIST][*]Maverick upgrade from updated Lucid install: **1300 packages, 2.3 GB**[/LIST]

That's a difference of one GB and 300 packages! I did expect differences but not to this extent. So much for upgrade vs. fresh install. :KS


Presumably though when you go from Hardy all the way up you have programs in that aren't in if you do default install, for example, GIMP isn't in Lucid default install, but was in Karmic and before?

Or am I being thick (again)

Also do upgrades add default programs or not, for example when you go hardy upgrading to Lucid, do you gain PitVi (or whatever it's called, the video editor)

---

### Post by MacUntu on 2010-05-17
> **taavikko said:**
> Out of curiosity, did ex. aptitude show obsolete packages?

The update manager removed a lot of obsolete packages, and I manually deleted any leftovers that were listed in "Obsolete or local" and "Auto removable" in Synaptic after each upgrade.

> **Arla said:**
> Presumably though when you go from Hardy all the way up you have programs in that aren't in if you do default install, for example, GIMP isn't in Lucid default install, but was in Karmic and before?

Yes, eg. I have GIMP and Pitivi, and Pidgin and Empathy. Of course I don't want those packages to get removed, I was just surprised by the amount of additional packages. :)

---

### Post by kansasnoob on 2010-05-17
Requests for change are seldom read at the forums!

It's a tough process:

[http://ubuntuforums.org/showthread.php?t=1482615](http://ubuntuforums.org/showthread.php?t=1482615)

I'll let you know how that goes :)

---

### Post by seeker5528 on 2010-05-17
> **LKjell said:**
> By the fact that some programs in there you do not need at all on a gnome system is what I call abusing.

And if you don't want those things, you turn of the option to treat recommends as dependencies, which seems to be something it was felt Software Center didn't need to provide an option for, but that's another story.

Including the common stuff expected with a KDE program, is not abuse, presumably most people, even if they are running a non-KDE variant of Ubuntu, when installing a KDE game would want the help to work, would want option to be able to adjust at least the audio properties and look and feel properties, have useful information displayed when the app crashes, etc... QT, Plasma, KDE base, and KDE workspace, not sure what virutuoso gets used for, so that might be a stretch. 

> With recommend field you can end with two packages that depends on each other in a circular way.

You end up with that anyway some times. Circular dependencies are a bug in their own right and should be dealt with during the development cycle, which I would expect to apply to recommends as well, since they are treated as dependencies by default.
 
>  It also means that there is a potential that some package can depends on those big meta packages. And you then end with a system that you really do not want.

I would expect that to be considered a bug as well. Is there an example of such a thing happening?

Later, Seeker

---

### Post by psusi on 2010-05-17
There is nothing wrong with circular dependency.  Whichever one you install pulls the other one in.

---

### Post by MacUntu on 2010-05-17
Wouldn't you just combine such packages?

---

### Post by xebian on 2010-05-17
> **LKjell said:**
> 

As the policy manual state the recommend should be packages which group together as a program. But Kigo and update-manage-kde has no relation except that they are kde programs.

You need to understand that all the kde apps are packaged and optimized for Kubuntu.  It's true you can install KDE apps in Ubuntu but you have to accept all the other baggages that come with it. The same thing is true when a Gnome apps is installed in Kubuntu.

If you like playing Go then you should consider the Gnome version which BTW is the only package recommended by kigo - gnugo.

```
Package: kigo
Priority: optional
Section: games
Installed-Size: 1640
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: amd64
Source: kdegames
Version: 4:4.4.2-0ubuntu1
Depends: kdebase-runtime (>= 4:4.4.2), kdelibs5 (>= 4:4.4.2), libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libkdegames5 (>= 4:4.4.2), libqt4-dbus (>= 4:4.5.3), libqt4-network (>= 4:4.5.3), libqt4-svg (>= 4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.6.1), libqtgui4 (>= 4:4.5.3), libstdc++6 (>= 4.1.1)
Recommends: gnugo
Filename: pool/main/k/kdegames/kigo_4.4.2-0ubuntu1_amd64.deb

```

Having separate packages for Gnome and KDE is a lot of work for maintainers though there are some.

---

### Post by seeker5528 on 2010-05-19
> **psusi said:**
> There is nothing wrong with circular dependency.  Whichever one you install pulls the other one in.

Typically the issues with circular dependencies don't surface until later, either when you try to install something else or try to upgrade, in most cases I would expect these types of issue to be caught before release, but probably too many variables to catch every issue. Also much more likely to be something you would run into an issue with during an upgrade than when installing additional software from an official repository for a release.

This is why they need people installing different things and testing upgrades from previous releases that have more installed than the basic Ubuntu, Kubuntu, etc....

One difference between dependencies and 'recommends as dependencies'....

You can't remove something that is a dependency of something else. If you remove something that is recommended by another package, you won't get a complaint, even if the option to treat recommends as dependencies is enabled.

 Later, Seeker

---

