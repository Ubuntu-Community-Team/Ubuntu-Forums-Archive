---
title: "Unified Application Menu Testing"
date: 2010-05-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-05-28
Time to start doing some structured testing of the [unified menu bar]("http://design.canonical.com/2010/05/menu-bar/") for UNE (which is also set to be optionally available for use on the regular Ubuntu desktop). 

Here's the wiki page with testing instructions (and other informative bits):

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationMenu](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationMenu)

---

### Post by ranch hand on 2010-05-28
Oh all right.  So I have picked an install as the victim for this.

We will see what comes of it.

I sure hope it is a better idea than Plymouth.

---

### Post by null_pointer_us on 2010-05-28
Will this be available in Maverick final for normal desktop users?

---

### Post by ranch hand on 2010-05-28
If you read the 2 links provided by 23meg you will discover that the answer is yes.

It is not all available quite yet.  There is one package that apt can't find, at least for the desktop folks like me.

---

### Post by cariboo on 2010-05-28
Change the repository to Lucid instead of Maverick to get the missing packages.

---

### Post by MacUntu on 2010-05-28
> **ranch hand said:**
> It is not all available quite yet.  There is one package that apt can't find, at least for the desktop folks like me.

You need to change the PPA's Distribution value to lucid.

Installs fine but nothing shows up when starting apps like mentioned.

---

### Post by ranch hand on 2010-05-28
If I understand what I am still in the process of reading on the wiki page, it should be all right in the maverick repo come the release of A1.

Is that right?

If so, I can wait.

---

### Post by wayneericgouin on 2010-05-28
I tried it in the maverick desktop and for the very few applications it works for it seems to be fine, other than having to run a separate command before the app command which i'm sure is only for now.

---

### Post by null_pointer_us on 2010-05-28
> **null_pointer_us said:**
> Will this be available in Maverick final for normal desktop users?

> **ranch hand said:**
> If you read the 2 links provided by 23meg you will discover that the answer is yes.

Where? (specifically)

The sentence starting with, "**So you can help with this testing**," doesn't fully address my question.

---

### Post by ranch hand on 2010-05-28
Well that is a tough question if you can't find it but is is mentioned in the wiki under, of all the cryptic headings, Ubuntu Desktop Installation.

---

### Post by null_pointer_us on 2010-05-28
So you skimmed my post, instead of reading it properly, then faulted me for not leaping to the conclusion that directions for adding a development PPA (specifically for testing a netbook feature) somehow means it will be available in the maverick desktop F-I-N-A-L repos?

> **Ubuntu Desktop Installation**

**For development purposes,** a gnome-panel compatible version is also available. 

---

### Post by ranch hand on 2010-05-28
No, you actually have to read the anouncement to find that and I am not going to count the lines for you.

---

### Post by cariboo on 2010-05-28
There are no F-I-N-A-L repos, they are the same as what we are using now.

---

### Post by null_pointer_us on 2010-05-28
> **cariboo907 said:**
> There are no F-I-N-A-L repos, they are the same as what we are using now.

Though it seems obvious, I was referring to the set of packages intended to be supported by the final release, not to whether there are separate testing and release repositories for Maverick.

Will this be available in Maverick final for normal desktop users?

---

### Post by null_pointer_us on 2010-05-28
> **ranch hand said:**
> No, you actually have to read the anouncement to find that and I am not going to count the lines for you.

So it is N-O-T in the wiki, as you said, where you said it was, but it is supposedly now in the announcement linked somewhere else in the wiki, but you decline to give any indication of where. Whatever.

---

### Post by ranch hand on 2010-05-28
The announcement is linked at the start of the wiki page.  When doing research links are actually considered part of the reading of a document.

---

### Post by cariboo on 2010-05-28
According to the wiki this is being developed for the UNE, which uses the same repositories, so yes they will be available for desktop users, just as the the UNE packages are now.

---

### Post by null_pointer_us on 2010-05-28
@ranch hand

First, you claimed it was in the wiki, in a very specific place, and reading that section confirmed that it had no answer to my question. Second, you changed your statement to a more general one, that it was in the announcement. I reread that one again, yet it provided no answer to my question (nor did it during the first reading).

Now, a reasonable person might assume the reason why I asked in the first place is because it wasn't in the two linked articles. And an honest person would not manipulate his own words after the fact. Your behavior indicates otherwise, and I find your attitude grating, so I'm adding you to my ignore list.

In lieu of any credible responses, I reread the two provided links again and found nothing, apart from confirmation that the stuff being made available on desktop edition now is just a testing release, which (by nature) may be pulled at any time including before final release of the desktop edition.

> **null_pointer_us said:**
> Will this be available in Maverick final for normal desktop users?

Taken from here:
[http://www.markshuttleworth.com/archives/359](http://www.markshuttleworth.com/archives/359)

> In the first few iterations of Ubuntu&#8217;s netbook-oriented UI, we concentrated on collapsing the window title into the top panel. In 10.10, we&#8217;re going to put the menu there.

**[SIZE="3"]Only on the Netbook Edition UI[/SIZE]**

We&#8217;re going to put the menu in the panel on the netbook edition of Ubuntu, and not on the desktop edition, because that&#8217;s where the screen real-estate is most precious.

Hardly a yes, but he goes on to say:

> However, it will be straightforward to use this on your desktop too, if you want, and we&#8217;d encourage people to try with that configuration. The more testing we have early on, the better we&#8217;ll understand how it works with different applications. It will be easy to add to the standard desktop panel for people who want to try it out, or prefer to work that way.

So that is a yes, in an article linked at the bottom of a one of the articles linked by the original poster. Not worth the time spent arguing about it, but whatever.

---

### Post by null_pointer_us on 2010-05-28
> **cariboo907 said:**
> According to the wiki this is being developed for the UNE, which uses the same repositories, so yes they will be available for desktop users, just as the the UNE packages are now.

Thanks, I did not realize that.

(BTW, there are two versions of the MenuBar, one for the Unity panel, and one for the gnome-panel (for testing), and the wiki did not say whether the gnome-panel part would be maintained.)

---

### Post by wayneericgouin on 2010-05-28
apt cant find appmenu-gtk even though it's listed as part of the UNE repo.

---

### Post by cariboo on 2010-05-28
[http://ubuntuforums.org/showpost.php?p=9375186&postcount=5](http://ubuntuforums.org/showpost.php?p=9375186&postcount=5)

---

### Post by anders_c_ on 2010-05-29
Tried to test it in lucid but i can't add it to the panel...does anyone have any screenshots?

---

### Post by MacUntu on 2010-05-29
Is this working for anyone using Maverick? Tested it on two systems w/o luck.

---

### Post by Universal344 on 2010-05-29
Does anyone know if this will be coming to Maverick repos soon?  Doesn't make sense that it would be available to Lucid before Maverick.

---

### Post by tad1073 on 2010-05-30
my question is, where do I put the environment variables.

---

### Post by cariboo on 2010-05-30
I just started up vlc, I didn't have to enter any extra parameters. See screenshot. BTW this is on my netbook.

---

### Post by ronacc on 2010-05-31
not working here on my maverick amd64 install , tried it with gnome terminal , opera and vlc ,no effect in any of them .

switched to metacity and gtk instead of compiz and emerald  ,no help

---

### Post by jppr on 2010-05-31
i have installed that in Linux Mint 9 and works fine. I look forward to an alpha1, do a clean installation, and then test system for in maverick.

---

### Post by bcbc on 2010-06-07
Just ran the latest updates and finally it's working on the regular 10.04 desktop install.

---

### Post by MacUntu on 2010-06-08
Hm, all I get in Maverick is "No Indicators" (I've run 'GTK_MENUPROXY="libappmenu.so" gedit'). The indicator applet is now in Maverick's universe repo.

**Edit: **
The PPA now also holds packages for Maverick.

**Edit 2: **
After a restart I'm seeing this:

> test@box:~$ GTK_MENUPROXY="libappmenu.so" gedit

** (gedit:1787): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed

:(

---

### Post by bcbc on 2010-06-08
This is where i deviated from the web instructions. I originally installed the appmenu-gtk from the lucid ppa, but set it back to maverick. I also put the GTK_MENUPROXY=xxx in /etc/environment.

---

### Post by null_pointer_us on 2010-06-09
It does nothing on my system.

I installed lucid packages from the ppa, then added the indicator-appmenu to the top panel. Nothing showed up, as the wiki says. Trying to add a second one to the top panel resulted in the delete-reload dialog boxes, also as the wiki says. This confirms that the panel applet is loading and running.

I tried putting GTK_MENUPROXY="libappmenu.so" in /etc/environment and logged out/in.

Nothing showed up in the top panel.

I tried opening a GTK program like nautilus or the calculator.

Nothing.

I tried changing the GTK_MENUPROXY to use an absolute path (/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so) and logged out/in.

Nothing.

I tried running gedit with the environment variable directly (GTK_MENUPROXY="libappmenu.so" gedit).

Nothing.

Occasionally, the top panel will flash a little and stuff will move around a few pixels in either direction, but no menu text (or any error text, for that matter) ever shows up.

EDIT: Changing the ppa source to maverick and rebooting caused a few packages to be upgraded. Now the applet crashes everytime a GTK window is opened -- same error as in MacUntu's post:

```
$ GTK_MENUPROXY="libappmenu.so" gedit

** (gedit:1787): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
```

---

### Post by bcbc on 2010-06-09
These are the versions I have installed:
appmenu-gtk 0.0.4-ubuntu1
libqtgui4 4:4.7.0~beta1+git20100522-0ubuntu2
indicator-applet-appmenu 0.4.2-0ubuntu1
indicator-appmenu 0.0.3-0lucid1

Also I think the guide is wrong when it says > Right click on the panel, and add the "Indicator Applet Appmenu" applet. Note: you won't see any change on the panel yet, but if you add the applet a second time it will exit so you can remove it (choose: delete & don't reload)

I actually did "don't delete" and "reload". I tried it now and it doesn't work if you follow the wiki instructions.

my /etc/environment:

```
$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
GTK_MENUPROXY="libappmenu.so"

```

---

### Post by echelon89 on 2010-06-09
> **null_pointer_us said:**
> It does nothing on my system.

I installed lucid packages from the ppa, then added the indicator-appmenu to the top panel. Nothing showed up, as the wiki says. Trying to add a second one to the top panel resulted in the delete-reload dialog boxes, also as the wiki says. This confirms that the panel applet is loading and running.

...

EDIT: Changing the ppa source to maverick and rebooting caused a few packages to be upgraded. Now the applet crashes everytime a GTK window is opened -- same error as in MacUntu's post:

```
$ GTK_MENUPROXY="libappmenu.so" gedit

** (gedit:1787): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
```
Same error for me

---

### Post by null_pointer_us on 2010-06-10
> **bcbc said:**
> These are the versions I have installed:
appmenu-gtk 0.0.4-ubuntu1
libqtgui4 4:4.7.0~beta1+git20100522-0ubuntu2
indicator-applet-appmenu 0.4.2-0ubuntu1
indicator-appmenu 0.0.3-0lucid1

Ah, this explains it. I have the same versions, except [COLOR="DarkOrange"]**indicator-appmenu**[/COLOR] is at **[COLOR="DarkOrange"]0.0.4-0ubuntu1[/COLOR]**.

EDIT: Now I believe my problem is that I installed from the PPA as a [COLOR="DarkOrange"]**lucid**[/COLOR] source, then switched it to a [COLOR="DarkOrange"]**maverick**[/COLOR] source and did an update (to see if that would fix my issues), but the maverick source still has no suitable indicator-appmenu:

```
$ sudo apt-get install --reinstall indicator-appmenu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of indicator-appmenu is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
```
When they finish updating the maverick packages in the PPA, it will probably fix my issues.

> Also I think the guide is wrong when it says 

I actually did "don't delete" and "reload". I tried it now and it doesn't work if you follow the wiki instructions.
Thanks, now it no longer crashes, but sadly it's back to doing nothing.

I will try again when there are new versions.

> my /etc/environment:

```
$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
GTK_MENUPROXY="libappmenu.so"

```

Thanks for clarifying; I'm using the same **[COLOR="DarkOrange"]GTK_MENUPROXY[/COLOR]** line now (but no change in indicator-appmenu's behavior).

---

### Post by castrojo on 2010-06-10
> **null_pointer_us said:**
> EDIT: Now I believe my problem is that I installed from the PPA as a [COLOR="DarkOrange"]**lucid**[/COLOR] source, then switched it to a [COLOR="DarkOrange"]**maverick**[/COLOR] source and did an update (to see if that would fix my issues), but the maverick source still has no suitable indicator-appmenu:

Yep, this will definitely break! Later on today there will be a new upload of all the appmenu stuff in Maverick, you'll need to remove the PPA as everything will be in Maverick now. (The PPA will be for Lucid only)

EDIT: Also we'll make it so you don't need the /etc/environment bits anymore.

---

### Post by bcbc on 2010-06-10
Just fyi, I installed everything except the appmenu-gtk from maverick, switched the ppa to lucid to install appmenu-gtk (as it didn't exist in maverick), and then switched it back to maverick. It didn't work at first, until my post - which was right after running some updates (but I didn't record what exactly got updated). So I'm not sure why my indicator-appmenu version says 'lucid'.

Also, I'm running it in lucid as well, and it seems way less stable than the way I have it working in maverick!!? which seems counter-intuitive. In lucid the indicator-appmenu-applet crashes a lot on startup, and the menus appear erratically (at least I haven't figured out the pattern yet).

Lucid behaviour (only):
start gedit, menu shows on panel
exit gedit
start gedit, menu doesn't show
exit gedit
start terminal, menu shows on panel
start gedit, menu shows on panel again
switch to terminal and back to gedit, menu switches
exit both
start terminal. menus doesn't show
no combination of starting terminal or gedit results in menu on panel
start a different app - calculator - help submenu shows
start gedit, menu still doesn't show
start terminal, menu shows
exit gedit, calculator, terminal
start calculator/gedit/terminal, menu doesn't show
etc.   ???

---

### Post by null_pointer_us on 2010-06-10
@ whiprush

Thanks, I have removed the PPA and will await the Maverick packages.

---

### Post by null_pointer_us on 2010-06-11
The packages became available, so I updated:

```
$ apt-cache policy indicator-applet-appmenu indicator-applet appmenu-gtk | grep Installed

  Installed: 0.4.2-0ubuntu1
  Installed: 0.4.2-0ubuntu1
```

Now the "No Indicators" text shows up and the applet does not crash.

However, it never picks up any menus. Putting the line back in /etc/environment had no effect; neither did running gedit from a terminal window nor doing the same with the GTK_MENU_PROXY="libappmenu.so" part. EDIT: I see the wiki has been updated, but it did not help. I'll try reinstalling those packages just to make sure.

EDIT 2: Oh, my bad. There is no appmenu-gtk on my mirror yet, so obviously the applet won't get any menus from gtk apps. :oops:

---

### Post by MacUntu on 2010-06-12
It now "works" in Maverick (GNOME session, w/o setting any environment variables), but I'm having problems with the menus initially not showing up completely (seems to work after a redraw like when switching to another application and back or minimizing and restoring the application). Also sometimes it works, then it stops working, works again, then it stops again (killing the panel helps). Can anyone confirm this?

[[img]http://img.xrmb2.net/155312.jpg[/img]](http://img.xrmb2.net/images/155312.png) [[img]http://img.xrmb2.net/903734.jpg[/img]](http://img.xrmb2.net/images/903734.png)

**Edit:**
Seems to work more(!) reliably within a Ubuntu Netbook Edition. Do items in submenus work for you guys? If not, add yourself to: [https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/592949](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/592949)

---

### Post by null_pointer_us on 2010-06-12
> **MacUntu said:**
> It now "works" in Maverick (GNOME session, w/o setting any environment variables), but I'm having problems with the menus initially not showing up completely (seems to work after a redraw like when switching to another application and back or minimizing and restoring the application). Also sometimes it works, then it stops working, works again, then it stops again (killing the panel helps). Can anyone confirm this?

I can confirm that it only works sometimes. Eventually it stops working altogether.

---

### Post by Gh0stDog on 2010-06-13
Hi,   I've got some problems in Lucid since a recent update. Gprename, Gftp and some others gnome applications are broken. Is this related to Unity or menuproxy only ?   See: [http://linux.aldeby.org/parcellite-crash-on-icon-click-zim-does-not-load.html/comment-page-1#comment-29548](http://linux.aldeby.org/parcellite-crash-on-icon-click-zim-does-not-load.html/comment-page-1#comment-29548)

---

### Post by ranch hand on 2010-06-13
Is this supposed to do much of anything?

It seems to be fine with 2 of the 13 apps I use regularly and does nothing with the others.  I realize that there needs to be changes in the apps to make this work but if the plan is to drop the dual menus at A2 there are going to be some problems.

Works great with gedit and transmission.  Not sure if I like it or not.  Have to see when there enough apps that it works with to really try it.  I think it may be real nice.

---

### Post by MacUntu on 2010-06-18
Can anyone confirm that the menu stopped working with recent updates? I updated this morning and everything worked fine, one reboot later invoking the menu causes a hang (no crash, just a half a minute long hang).

---

### Post by frustphil on 2010-06-18
> **MacUntu said:**
> Can anyone confirm that the menu stopped working with recent updates? I updated this morning and everything worked fine, one reboot later invoking the menu causes a hang (no crash, just a half a minute long hang).

I am experiencing that too. Using Netbook Edition.

---

### Post by MacUntu on 2010-06-18
This is fixed with appmenu-gtk 0.0.7-0ubuntu2.

---

### Post by ranch hand on 2010-06-19
Seems to be working better all the time.

I do wonder exactly why we need this.

---

### Post by cariboo on 2010-06-19
On a desktop system you don't need the unified menu, but on a netbook where vertical space is at a premium, every little bit helps. Once the appmenu is dome, the window will loose the top menu bar, and all the functions will be integrated into the top panel on a per application basis. The double menus are just for troubleshooting purposes. All the ui changes are aimed at the UNE this release.

---

### Post by ranch hand on 2010-06-19
Ah, I see.  I do not have, nor want, a netbook.  I do however have the UNE installed here on my desktop box.

I do not have this installed there as there seems to be plenty of problems there right now without something else.  I can see how this would be a nice deal with a smaller screen.  Hadn't thought about it.

UNE, by the way, has impressed me with the way it works.  If they get a menu like the gnome main menu in there somewhere it is juat a whole lot better than what I have seen with Gnome Shell.  It is a little buggy right now but you can use it and see how it is supposed to work.  Pretty slick.

I may try the edgers stuff on that install.  All my problems seem to be graphic problems.  Maybe a more advanced driver would help.

Thanks.

---

### Post by MacUntu on 2010-06-20
Could also help people that fell for this 1366*768 crap resolution on real notebooks. I had a 14.1" notebook with a 1280*768 panel and it was a pain even when just browsing the web.

---

### Post by Nr90 on 2010-06-20
It does work for me, kinda.
Not a lot of apps that show anything useful, but for terminal and transmission it works pretty well.

---

### Post by hugmenot on 2010-06-20
> **cariboo907 said:**
> On a desktop system you don't need the unified menu, but on a netbook where vertical space is at a premium, every little bit helps.

On my laptop – having 900 screen lines – vertical space is at a premium too, and I very much welcome the effort to make it usable on regular desktops, too.

---

### Post by uBeer on 2010-06-20
Does anyone notice the extra separation lines in some of the menus? Some of them are because there are missing menu entries, but some of them seem to come out of nowhere. Noticeable in Banshee, Gimp, Epiphany and others.

---

### Post by seeker5528 on 2010-06-21
> **ranch hand said:**
> I do not have this installed there as there seems to be plenty of problems there right now without something else.  I can see how this would be a nice deal with a smaller screen.  Hadn't thought about it.

Some people just like to have a common menu, in particular if they are used to Apple systems.

KDE used to have the option in 3.x that worked pretty well, have not looked for it in 4.x to see if it carried over or not.

EDIT:

For KDE it looks like the [xbar plasmoid](http://packages.ubuntu.com/intrepid/kde/plasmoid-xbar) would be the thing, [screenshot](http://kde-look.org/content/preview.php?preview=2&id=81224&file1=81224-1.jpg&file2=81224-2.jpg&file3=&name=KDE+4.2+with+two+panels+%26+XBar+menubar&PHPSESSID=bd6046e09909f2109c82c68f99861fa1).

Later, Seeker

---

### Post by castrojo on 2010-06-25
Reposting my status update from here: [https://lists.launchpad.net/ayatana-dev/msg00006.html](https://lists.launchpad.net/ayatana-dev/msg00006.html)

Not to be outdone by the (excellent) work of the other Unity folks,
Ted and Cody have released indicator-appmenu 0.0.7 and appmenu-gtk
0.0.8 which are now in Maverick and the Lucid PPA.

Overall:

We're getting close to including the menu by default in Unity (right
now you have to explicitly install it). There's a few issues left to
iron out, basically submenus and some still-partial menus. That's
where the focus is right now. Seb128 and didrocks will then determine
when to flip the menu on as default. The DX team are going through
existing bugs right now, so now would be a good time to double check
an issue to see if it still affects you.

Appmenu-gtk
- Seperators work as expected (no more extra seperators in the menus)
- Keyboart shortcuts are now displayed in the menu
- Crasher fixes

Changelogs:
[https://code.launchpad.net/~indicator-applet-developers/indicator-appmenu/trunk](https://code.launchpad.net/~indicator-applet-developers/indicator-appmenu/trunk)
[https://launchpad.net/ubuntu/+source/indicator-appmenu/0.0.7-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-appmenu/0.0.7-0ubuntu1)

[https://code.launchpad.net/~canonical-dx-team/appmenu-gtk/trunk](https://code.launchpad.net/~canonical-dx-team/appmenu-gtk/trunk)
[https://edge.launchpad.net/ubuntu/+source/appmenu-gtk/0.0.8-0ubuntu1](https://edge.launchpad.net/ubuntu/+source/appmenu-gtk/0.0.8-0ubuntu1)
[https://edge.launchpad.net/ubuntu/+source/appmenu-gtk/0.0.8-0ubuntu2](https://edge.launchpad.net/ubuntu/+source/appmenu-gtk/0.0.8-0ubuntu2)

And of course, our home page with instructions on how to test:
[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationMenu](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationMenu)

---

### Post by castrojo on 2010-07-09
Hi everyone,

Another week, another release of the new menu for UNE. This week indicator-appmenu did not have any releases, as the bugs reported have been in appmenu-gtk. Cody Russell has released 0.1.1 of appmenu-gtk, which is in Maverick and currently building for the Lucid PPA. Here are the highlights:

- Bullets should now appear as bullets instead of checkmarks
- Fix errors in GIMP

Full changelogs: [https://launchpad.net/ubuntu/maverick/+source/appmenu-gtk/0.1.1-0ubuntu1](https://launchpad.net/ubuntu/maverick/+source/appmenu-gtk/0.1.1-0ubuntu1)

Note that if you are using Unity that there is a mutter bug that breaks submenus that might be confused for an appmenu bug, please see: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/592949](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/592949)

The menu itself is in pretty good shape right now, unless someone has any objections we’d like to turn the double menus off in the applications for next week’s release. Special thanks to Hernando Torque for his detailed bug reporting for the menus!

---

### Post by gnomeuser on 2010-07-09
Excellent, I just switched the appmenu to only display the global menu. It now totally replaces the globalmenu-applet for me and saves me the time to hack that down to size for my purposes.

No major errors to report, it seems to flicker every now and again but works okay.

---

### Post by castrojo on 2010-07-09
> **gnomeuser said:**
> Excellent, I just switched the appmenu to only display the global menu. It now totally replaces the globalmenu-applet for me and saves me the time to hack that down to size for my purposes.

Yeah we had a call with the global menu guys and they really helped out pointing out problems they've had, etc.

> No major errors to report, it seems to flicker every now and again but works okay.

In Unity or normal GNOME?

---

### Post by Merk42 on 2010-07-09
Is there any way the UNE developers can talk to the Virtualbox developers about the Mutter requirements so it can actually run in Virtualbox?

---

### Post by castrojo on 2010-07-09
> **Merk42 said:**
> Is there any way the UNE developers can talk to the Virtualbox developers about the Mutter requirements so it can actually run in Virtualbox?

AFAIK vbox doesn't run mutter-based things well, but wasn't able to find a bug report in their bug tracker about it, do you know if anyone's reported the bug? (I can't seem to find one)

---

### Post by Merk42 on 2010-07-09
> **whiprush said:**
> AFAIK vbox doesn't run mutter-based things well, but wasn't able to find a bug report in their bug tracker about it, do you know if anyone's reported the bug? (I can't seem to find one)
I know VB has a problem with Mutter, and I don't know of any bug report. That's basically what I was asking about.

---

### Post by castrojo on 2010-07-09
The best way to get developers talking is to start with a bug report, then getting people who use virtualbox to add their data (perhaps gnome-shell users or something).

If it's been this long and there hasn't been a bug report then I would guess most people testing this stuff are either using KVM or real hardware.

---

### Post by gnomeuser on 2010-07-09
> **whiprush said:**
> Y

In Unity or normal GNOME?

Normal GNOME but the machine is acting strange so I will give it a few days, perhaps just a quirky update.

---

### Post by hugmenot on 2010-07-09
Is the app-menu only this slow for me? It takes 3 seconds to show up for a Nautilus window:
[IMG]http://launchpadlibrarian.net/51595657/slow-nautilus.gif[/IMG]
Also note the CPU spike.

Bug here: [https://bugs.launchpad.net/ubuntu/+bug/603365](https://bugs.launchpad.net/ubuntu/+bug/603365)

---

### Post by castrojo on 2010-07-15
[http://castrojo.tumblr.com/post/817490854/application-menu-status-for-15-july](http://castrojo.tumblr.com/post/817490854/application-menu-status-for-15-july)

Boring week this week, thanks for the bug on the nautilus slow-menu.

---

### Post by hugmenot on 2010-07-16
One question, not sure if that’s a bug or a not implemented feature:

How do I access the app-menu with the keyboard? Normally I’d expect to use Alt-F for «File», Alt-E for «Edit», etc. Those do nothing, atm.

---

### Post by cariboo on 2010-07-16
I just updated, the keyboard shortcuts work on some apps.

---

### Post by hugmenot on 2010-07-17
> **cariboo907 said:**
> I just updated, the keyboard shortcuts work on some apps.

Which, for example?

---

### Post by MacUntu on 2010-07-17
Shortcuts do work, but opening the menus doesn't (obviously tested with APPMENU_DISPLAY_BOTH=0).

---

### Post by x-shaney-x on 2010-07-17
> **MacUntu said:**
> Shortcuts do work, but opening the menus doesn't (obviously tested with APPMENU_DISPLAY_BOTH=0).

Just wondering where that variable can be changed :)

<EDIT>
Nevermind, found it

---

### Post by seeker5528 on 2010-07-19
I file a bug report if somebody wants to try this and confirm the behaviour.

Create a .desktop file in '/usr/share/xsessions/' with the contents of:

```
[Desktop Entry]
Name=Default Xsession
Comment=This runs ~/.xsession
Exec=/etc/X11/Xsession
```

:I called it default.desktop on my system.

Then create a '.xsession' file in your home directory with the contents of:

```
exec /usr/bin/gnome-session
```

Then log out and change your session from 'Ubuntu Desktop Edition' to 'Default Xsession' and log back in.

On my system the panel applet works if I use the normal 'Ubuntu Desktop Edition', but if I use my 'Default Xsession' the panel applet never re-acts to the loading of any applications. 

There is a screenshot attached to the bug report.

[https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/607463](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/607463)

Later, Seeker

---

