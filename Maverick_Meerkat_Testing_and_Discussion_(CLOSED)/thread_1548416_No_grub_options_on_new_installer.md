---
title: "No grub options on new installer"
date: 2010-08-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by davideotape on 2010-08-08
I've just got round to re-installing ubuntu after accidentally wiping it the other week. However, the new installer doesn't seem to have any grub options. I need the one which allows you to install grub to a partition instead of a hard drive. Does anyone know how I can do this?

[Bug Report]("https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/615033")

---

### Post by ranch hand on 2010-08-08
When I did ISO testing the option was there on the screen where you OK installation labelled "advaced" as it has always been.

I did however file a bug on it as it did not work right.  I did not want it install on any thing and marked it so.  It did not install.  It did ruin the grub installed on the MBR so that nothing could boot.

After installation and getting the right grub back on the MBR I fooled with the new install a bit and got some errors when running update-grub.  The only file in /boot/grub was grub.cfg.  At that time purging grub-pc and grub-common and making sure that the /boot/grub file was deleted then reinstalling got me a total of 2 files in /boot/grub.

I did a transplant from another installation of 10.10.

I have done the same thing yesterday on 2 other, older, 10.10 installs with no problem.

As there seems to be a number of problems with the installation of grub it is a good thing you filed on that.  I wonder if anyone else had that problem.

I never get the release ISO as I have installed the testing one several times and just don't fool with it.  Plenty of other eyes on that.

---

### Post by dino99 on 2010-08-08
confirmthat initial grub2 installation is a nightmare, but reinstalling or upgrading work fine on my end, seem that it dont find previous partitioning

---

### Post by davideotape on 2010-08-09
Grub2 has always installed fine for me, but it's just I can't find the option that lets me choose where to install it, or even an option that doesn't install grub2 at all.

---

### Post by ronacc on 2010-08-09
it is on the last screen before the install actually begins , down at the bottom is a button labeled "advanced" that takes you to the screen where you can specify where you want grub installed .

---

### Post by davideotape on 2010-08-09
No, that's where it used to be. They've changed the installer now.

---

### Post by ronacc on 2010-08-09
Hmm I just installed lubuntu A3 and it was there , I guess I'd better grab a daily and have a look .

---

### Post by davideotape on 2010-08-09
> **ronacc said:**
> Hmm I just installed lubuntu A3 and it was there , I guess I'd better grab a daily and have a look .

Yep, it didn't change in time for A3. I downloaded a daily yesterday and the changes are there.

---

### Post by ronacc on 2010-08-09
looks like todays daily is screwed bigtime at least for me , the only thing that works is check disk , which reports no errors , try without installing boots to the gdm background with no panels , rt click menu , basicly brain dead . install acts exactly the same way ,seems to try to boot to desktop .

---

### Post by davideotape on 2010-08-09
Hmm, seemed to be working absolutely fine for me apart from the grub issues. Must say I do like the new ubiquity (apart from its numerous bugs)

---

### Post by kansasnoob on 2010-08-09
Thanks for filing that bug report. I subscribed so hopefully we'll hear something from the devs.

Based on what ronacc said about today's daily I'll probably wait until at least the end of the week before I try a new daily.

Loads of changes in ubiquity should make Beta iso-testing quite interesting ;)

---

### Post by VMC on 2010-08-09
> **ronacc said:**
> looks like todays daily is screwed bigtime at least for me , the only thing that works is check disk , which reports no errors , try without installing boots to the gdm background with no panels , rt click menu , basicly brain dead . install acts exactly the same way ,seems to try to boot to desktop .
I have a similar problem. Have had since the updated Ubiquity.
I have a nVidia GeForce 6150 SE. I know that must be the issue, but for the life of me I can't find a work around. On a old laptop I have ATI and using "radeon.modeset=0 xforcevesa" I can at least get that to boot.

There must be a similar mode command for nVida. Tried "nomodeset" still fails.

I am right now getting the var log files together to file a bug report.

This happens only when trying to install the latest ISO with the update Ubiquity installer.

---

### Post by cariboo on 2010-08-09
See [this]("http://ubuntuforums.org/showthread.php?t=1549195") thread, it may be the cause of the problems you are having.

---

### Post by kansasnoob on 2010-08-09
I was looking to see if I could find any "snapshots" of what the ubiquity changes are supposed to look like, and I've not found anything yet, but I got a chuckle out of one line in the changelog (highlighted in red):

> ubiquity (2.3.4) maverick; urgency=low

  [ Mario Limonciello ]
  * Also set the custom title when translating widgets.
  * If there is at least one framebuffer device, fallback to fbdev rather
    than vesa for bulletproof X.
  * Remove extra imports in ubiquity-dm.
  * Add a new template ubiquity/force_failsafe_graphics intended to force
    installation to use vesa or fbdev, but not on the target system.  This is
    primarily intended for systems where the installation kernel has known
    graphics problems, but you are solving them in a post installation step.
  * Fix packaging to install the new pieces introduced for the overhaul.
  * debian/control: fix build-deps from redesign branch.
  * install two new png files for the language page in the gtk frontend.
  * Fix automatic mode in gtk_ui.
  * Add a new controller function to allow disabling the progress_section
    of the Window for pages it doesn't make sense on that might be shown
    in automatic mode before the partitioner comes.
  * Move the call to unmount_source back into install.py, it's only really
    used there for file copy, not by plugins.
  * Update some DebconfFetchProgress calls to DebconfAcquireProgress calls.
  * Run success cmd after plugininstall finishes.
  * Correct a few more deprecated apt calls.
  * Don't show the warning page or the prepare page in oem-config for now.
    The prepare page might make sense to re-enable, but will need a little
    different wording if so.
  * Update deprecated use of get_release_name() to get_release().name.
  * Mark timezone to come after both partman and language so that it shows
    up in oem-config too.
  * Only run plugininstall after the last page in oem mode.
  * If the slideshow doesn't exist, hide the page notebook rather than
    showing the webkit 404 page.

  [ Bilal Akhtar ]
  * debian/ubiquity.templates:
    - Add an underline symbol before the label of the install button
      to make it accessible with the Alt key. (LP: #492825)

  [ Evan Dandrea ]
  **[COLOR="Red"]* Merge maverick-redesign branch.  Fingers crossed.[/COLOR]**
  * Automatic update of included source packages: clock-setup
    0.103ubuntu1.

 -- Evan Dandrea <evand@ubuntu.com>  Fri, 06 Aug 2010 14:15:17 -0400


---

### Post by cariboo on 2010-08-09
There are some screenshots at OMGubuntu, but I don't want to link them, as they are so frequently wrong. :)

---

### Post by ronacc on 2010-08-09
middle of my work day right now I'll beat on this more tonight .

---

### Post by VMC on 2010-08-09
> **cariboo907 said:**
> See [this]("http://ubuntuforums.org/showthread.php?t=1549195") thread, it may be the cause of the problems you are having.

Hopefully that's the cause of my problem.

With the new Ubiquity I get the following lines from the weird small 3-line terminal they now have attached to the install dialog:

```
Ubiquity 2.3.4
** Message: pygobject_register_sinkfunc is deprecated (GtkWindow)
** Message: pygobject_register_sinkfunc is deprecated (GtkInvisible)
** Message: pygobject_register_sinkfunc is deprecated (GtkObject)
exception: <urlopen error [Errno 110] Connection timed out>
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <> line 149.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <> line 149.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <> line 149.

```

It starts installing then stop and the lines above are what is reported. I'll have to look at those perl lines and see if that helps. Right now using todays ISO, I can't even get to the install option. No X.

---

### Post by cariboo on 2010-08-09
I got those same errors doing updates this morning on my two desktop systems, and those plus quite a few more updating my netbook, mostly related to the Software Center, which I rarely use.

---

### Post by pulpo69 on 2010-08-09
i did a fresh alpha3 install today, grub is now workng fine.
but i don't know where grub was installed, in mbr or not.

---

### Post by VMC on 2010-08-09
> **pulpo69 said:**
> i did a fresh alpha3 install today, grub is now workng fine.
but i don't know where grub was installed, in mbr or not.
Boot_info_script will tell that that. Refer to my "blue" link at the bottom of this post.

---

### Post by ronacc on 2010-08-09
tried again , it looks like they screwed more than just no grub options , by hitting F6 at the menu screen and selecting nomodeset I was able to get to the live desktop and try to install , things went from bad to worse .
please off me non-free ..........    should be offer not off
asks to select wireless network but none shown even though I have 2 and was actually connected to one at the time ( installing from live cd desktop ).
downloaded and installed updates during installation even though that option was NOT selected  and then hung at "retrieving file 18 of 18 ", skip option was greyed out. 
aborted installation but it had already  installed everything but the grub files 
rebooted live cd and tried again without any network connected so it couldn't try to d/l anything , strange, I was installing to sdd the first time now the same drive is called sdb ( I can tell from the size and arrangement of the partitions ) also it wiped out the labels for the partitions . well this time it still tried to d/l updates even though it was not connected to any network , skip still greyed out .waited 30 min for it to timeout trying to d/l unasked for updates with no network connection  , aborted second install attempt .
I think they need some serious work on this one . added comment to bug report .

---

### Post by VMC on 2010-08-09
> **ronacc said:**
> tried again , it looks like they screwed more than just no grub options , by hitting F6 at the menu screen and selecting nomodeset I was able to get to the live desktop and try to install , things went from bad to worse .
please off me non-free ..........    should be offer not off
asks to select wireless network but none shown even though I have 2 and was actually connected to one at the time ( installing from live cd desktop ).
downloaded and installed updates during installation even though that option was NOT selected  and then hung at "retrieving file 18 of 18 ", skip option was greyed out. 
aborted installation but it had already  installed everything but the grub files 
rebooted live cd and tried again without any network connected so it couldn't try to d/l anything , strange, I was installing to sdd the first time now the same drive is called sdb ( I can tell from the size and arrangement of the partitions ) also it wiped out the labels for the partitions . well this time it still tried to d/l updates even though it was not connected to any network , skip still greyed out .waited 30 min for it to timeout trying to d/l unasked for updates with no network connection  , aborted second install attempt .
I think they need some serious work on this one . added comment to bug report .

I saw that 18 of 18 several times. I was able to now install mine with the use of some voodoo. Read my post [here]("http://ubuntuforums.org/showpost.php?p=9700358&postcount=17") for how I installed Maverick. The reason behind using the terminal was a last hitch effort to see if more errors messages came way.

Now that I think about it, by unplugging the internet and waiting, gives Ubiquity time to settle down and complete. 
Its just a wild theory.

---

### Post by ronacc on 2010-08-09
I did try waiting it out , the 2nd time I had no network connection and waited 30 min but it never quit trying to d/l the updates so I gave up , maybe tomorrows daily:(

---

### Post by VMC on 2010-08-10
> **ronacc said:**
> I did try waiting it out , the 2nd time I had no network connection and waited 30 min but it never quit trying to d/l the updates so I gave up , maybe tomorrows daily:(
Your right, tomorrows another day, but I have tried this nonsense several more times now.

Odd but now I can boot to live system without intervention. Then I do have to open a terminal and type ubiquity and go from there. What I normally do is let it find my locale first then unplug the internet. The last time I just let it choose what ever with internet not connected. When it goes to the wireless dialog I waited. There's a message "ready when you are" at the bottom. I don't believe it so I wait a while longer. Then I click on "Forward" from the wireless dialog box. Presto it continues to completion. 

I'm waiting for the new X before I even consider filling a bug report on this. Besides the new Ubiquity is being worked on. Several issues, like the wireless dialog without anything in it. And the "skip" button that's grayed out. Kind of reminds me of the Winchester Mystery House... Places leading to nowhere.

---

### Post by ronacc on 2010-08-10
I still have my original upgraded from lucid install that I'm holding off updating until the Xserver gets sorted out , also jaunty , koala and suse on that box ,so I'll just keep throwing daily's at it until something sticks . I get that ready when you are but when I hit forward it stalls at the next screen , the progress bar stops at about 80% and the blurbs just keep repeating telling me how wonderful it will be when the install finishes . I'm not sure I like that "feature" too much like MS " Oh I'm great , Oh I'm great " .

---

### Post by davideotape on 2010-08-10
Report bugs for every issue you've found with Ubiquity. I filed at least 5 yesterday and I didn't even install ubuntu :P

---

### Post by Nesaskewatch on 2010-08-10
> **VMC said:**
> Odd but now I can boot to live system without intervention.

Even odder?  I can use the live dvd just fine without doing anything.  It just won't install.  Drag because my function keys now work as well! I hope that part sticks around.  

> **VMC said:**
> What I normally do is let it find my locale first then unplug the internet. The last time I just let it choose what ever with internet not connected. When it goes to the wireless dialog I waited. There's a message "ready when you are" at the bottom. I don't believe it so I wait a while longer. Then I click on "Forward" from the wireless dialog box. Presto it continues to completion.

I have tried with and without Internet at various points during install to no avail.  I did get the "ready when you are" only once however, but it made no diff.  The install is present in the partitions, but no entry in grub to select at boot.  I'm going to try replacing the suspect file with the Lucid version and see what happens.

This is fun!

---

### Post by ronacc on 2010-08-10
> **davideotape said:**
> Report bugs for every issue you've found with Ubiquity. I filed at least 5 yesterday and I didn't even install ubuntu :P

please link your bugs so that we can confirm and "me too" them .

@ Nesaskewatch  I tried copying the grub stuff from my other mangy install and adding the appropriate boot stanza , no luck it gets about 20 or 30 terminal lines into the boot and the kernel panics .

---

### Post by davideotape on 2010-08-10
[LIST]
[*][Can't choose where to install grub in ubiquity]("https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/615033")
[*][Some text on warning page can't be seen]("https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/615034")
[*][Ubiquity says I'm connected via ethernet, when I'm connected via wireless]("https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/615036")
[*][Typo in "Preparing to install Ubuntu"]("https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/615036")
[/LIST]

---

### Post by ronacc on 2010-08-10
confirmed one that wasn't yet , 2 are already triaged so they are working on this .

---

### Post by ronacc on 2010-08-10
zsync'd todays daily , no changes , still no grub choice , spelling errors , wireless not shown etc etc .

---

### Post by kansasnoob on 2010-08-10
> **ronacc said:**
> zsync'd todays daily , no changes , still no grub choice , spelling errors , wireless not shown etc etc .

Not much point until we see a change in the package 'ubiquity' ;)

I didn't even know we had a redesign coming. From what I've seen this could be a real nightmare.

I've seen no talk about it on Ayatana. Sometimes I wonder how much dev time is wasted just reproducing info for all the different teams, sub-teams, and sub-sub-teams, etc.

From what I've seen, Ara Pulido and the QA team just "get it" in general. They make things fairly straight forward and mostly seamless.

IMHO the devs could learn a lot from Ara :D

I hope towards late fall or early winter I'll be able to participate more in the QA process.

---

### Post by Nesaskewatch on 2010-08-10
> **ronacc said:**
> @ Nesaskewatch  I tried copying the grub stuff from my other mangy install and adding the appropriate boot stanza , no luck it gets about 20 or 30 terminal lines into the boot and the kernel panics .

Understood.

---

### Post by Manikris on 2010-08-10
Hi , 
The same kinda problem for me as well .. I installed ubuntu 10.04 after wiping it by mistake last week ... When i install , there s no option in the cd asking for installation side by side with my win 7. I selected the partitions manually 
Now , grub is not installed ...ie . when i power on my machine , it directly goes to win 7

can anyone help please ?

---

### Post by VMC on 2010-08-10
> **Manikris said:**
> Hi , 
The same kinda problem for me as well .. I installed ubuntu 10.04 after wiping it by mistake last week ... When i install , there s no option in the cd asking for installation side by side with my win 7. I selected the partitions manually 
Now , grub is not installed ...ie . when i power on my machine , it directly goes to win 7

can anyone help please ?
Are you sure you meant 10.04 and not 10.10. For Lucid, 10.04, ubiquity works fine. I 'zsync' it everyday and at the "Advance" tab you can change where or if grub gets installed.

---

### Post by subixonfire on 2010-08-11
This new installer must be drunk! :-)
Tried with today's daily:
if you select install on the first screen (on vmware or Normal  machine, vga - ati radeon 4355hd) resolution is set to 800X600 but the installer when you need to select the timezone resizes and doesn't fit on the screen, and you cant see the butons... if you click on the end of the screen uper border of the buttons then it takes you to next page.. ps: i'm connected to network wia lan but installer shows me as not connected.. Dead end

if you select try ubuntu then manually change screen resolution to bigger one, then its even more weird, It shows the wirelless screen with no networks, but i dont have a wifi dongle pluged in to my machine??? Then it shows some partition menager bug, that can be worked around by using gparted prior to install and making a partition table + one Big ext4 partition, & then freezes on copping files... but the installer looks normal after waiting for 15 minutes i saw an "!" mark in the status bar (near the clock) after clicked tells me that ubiqity has closed unexpectedly but ubiquity is still there frozen.. end then some "eye candy" for  the end.. The installer is smaller after run from live desktop, but you have two scrollbars... This scrollbars allow you to display all the text & image when of ubuntu commercials :-), but the logo of ubuntu or other apps mows along with the scrollbars...

ps:my English is bad and i know that :-)
IL post some screen shots later today..

---

### Post by ronacc on 2010-08-11
yes the new installer is a work in progress .

---

### Post by subixonfire on 2010-08-16
ok, zsynced todays daily installer worked fine =D>
ps: like the new installer allot, Maybe I'll post video on youtube..

---

### Post by x-shaney-x on 2010-08-16
Does anyone know if the lack of grub install is an actual bug or proposed "feature"?

---

### Post by 23meg on 2010-08-16
> **x-shaney-x said:**
> Does anyone know if the lack of grub install is an actual bug or proposed "feature"?

According to [the spec]("https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v"), the advanced partitioner (and *not* the other modes) should let you choose where to install the bootloader.

---

### Post by VMC on 2010-08-16
> **23meg said:**
> According to [the spec]("https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v"), the advanced partitioner (and *not* the other modes) should let you choose where to install the bootloader.

In real use it doesn't. It hasn't since the new Ubiquity. Hopefully in the future it will allow to into or not install grub.

---

### Post by kansasnoob on 2010-08-27
I thought I'd bump this because I'm still not seeing many of the necessary options with this new ubiquity.

I've mostly been watching the ubiquity changelog and testing the daily with VirtualBox but this evening I tried installing the Aug 26 daily (i386) in a dual drive machine and even after clicking on "manual" almost no needed options are available.

IMHO this is looking like a total nightmare!

For that matter I raised quite a fuss about "hiding" the boot options with a couple of silly "emblems" indicating that human action is needed - within three freakin' seconds!

It feels to me like we're turning Ubuntu into a "for techies only" distro! And I don't like that :(

The Beta (the one and only beta) is due in one week and I'm an iso-tester. I'm glad I'm well stocked on discs because I anticipate a lot of reworking of isos :D

I would however appreciate any feedback if I'm overlooking something.

---

### Post by Cenotaph on 2010-08-27
well, i was just about to come here and ask about this, so im glad you bumped this one.

should i use the alternate CD to install grub to a partition (or not install it at all) or is there a proper method to achieve this with the current desktop iso?

---

### Post by kansasnoob on 2010-08-27
I see there are some updates in ubiquity today but it'll be a while before I can actually test drive it.

I did run through a VirtualBox install and still see no "grub-install" options but I'll need to try an actual multi-drive install to check it out further.

---

### Post by ronacc on 2010-08-27
the option of where to put grub is gone but I will note that it did install grub to the MBR of the drive I had installed Ubuntu to (sdc) and did not default to sda as in the past .

---

### Post by dino99 on 2010-08-27
> **ronacc said:**
> the option of where to put grub is gone but I will note that it did install grub to the MBR of the drive I had installed Ubuntu to (sdc) and did not default to sda as in the past .

thats what ive requested to Colin when ive mailed him: grub have to be installed into the current ubuntu to not overwrite other distro. (maybe he have heard and understood the logic ;)

---

### Post by kansasnoob on 2010-08-27
I just did a trial install to my /dev/sdb which is an internal 80GB drive that I use for iso-testing and such, and grub installed to the mbr of /dev/sda (my 500GB internal). No option to do otherwise.

Hopefully they'll put that option back in some manner. It really doesn't effect me because I know very easily how to hand boot off to any other OS (except Mac), but I know some folks don't like to overwrite their Windows mbr and would rather install grub to a pbr and use Easy BCD, or just change boot order in BIOS.

Also. I miss the final review. That was a handy sanity check just to be sure no errors were made during the process :)

Now it just begins the install as soon as you've completed the username & password fields.

Another thing I noticed was that the windows can no longer be maximized or even expanded by dragging, kind of a bummer if you have a complex partitioning arrangement or if you're visually impaired like me :(

Oh, and ran into another bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/625258](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/625258)

---

### Post by cariboo on 2010-08-27
I did an install from todays daily live, aside form not giving you a choice of where to install grub, there isn't an option to change your computer name, with 8 systems in use, it a lot easier to keep track of them by name than it by ip address.

I found another couple of oddities, when you first get the screen that gives you a choice whether to install or try, the indicator-applet-session and sound icons were on the left side of the upper panel. Some of the installation screens are the right size, but once you get to the actual install you have to use the scroll bar to see the contents of the window.

The one good thing about there being no choice on where to put grub, at least new users can't accidentally install it on their Windows partition. Grub found all my partitions and listed them in the menu with no problem.

---

### Post by ranch hand on 2010-08-28
I did an install of Unity just now.  Finally got an ISO that would work.

Booted to the ISO on my second internal with the first turned off in bios.  This makes the second drive sda.

Booting with the external drive turned on makes it sdb and sdc.

Installed on sdb.  Grub installed on sda.  This is not a good thing.  Will have to boot using that menu.  This is tough.

Now, to boot my internal drive I need to have the external on or I have no grub.  This is stupid at best.
 
This is my /boot/grub/grub.cfg file.  You may find it amusing to wad through this, I do not. 
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos18)'
search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos18)'
search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos18)'
    search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=426c9e71-43da-47b0-80c6-d91a6761e08a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos18)'
    search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=426c9e71-43da-47b0-80c6-d91a6761e08a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos18)'
    search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos18)'
    search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos18)'
    search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos18)'
    search --no-floppy --fs-uuid --set 426c9e71-43da-47b0-80c6-d91a6761e08a
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "9.04-32 on sda6 (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "9.10-32 on sda8 (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /vmlinuz root=/dev/sda8 ro quiet splash
    initrd /initrd.img
}
menuentry "10.04-32 on sda10 (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "9.04-64 on sda12 (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "9.10-64 on sda14 (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "10.04-64 on sda16 (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /vmlinuz root=/dev/sda16 ro quiet
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=3ea55cf0-91ef-4451-b653-0226c5496276 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=3ea55cf0-91ef-4451-b653-0226c5496276 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=3ea55cf0-91ef-4451-b653-0226c5496276 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=3ea55cf0-91ef-4451-b653-0226c5496276 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3ea55cf0-91ef-4451-b653-0226c5496276 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 3ea55cf0-91ef-4451-b653-0226c5496276
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3ea55cf0-91ef-4451-b653-0226c5496276 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Stoner1.2 on sda8 (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set d4e5d7ce-da7e-403e-9eb5-bf4b4d40522a
    linux /vmlinuz root=/dev/sda8 ro quiet
    initrd /initrd.img
}
menuentry "Sid on sda6 (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set d4e5d7ce-da7e-403e-9eb5-bf4b4d40522a
    linux /vmlinuz root=/dev/sda6 ro quiet
    initrd /initrd.img
}
menuentry "Squeeze on sda8 (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set d4e5d7ce-da7e-403e-9eb5-bf4b4d40522a
    linux /vmlinuz root=/dev/sda8 ro quiet
    initrd /initrd.img
}
menuentry "10.04-32 on sda10 (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set d4e5d7ce-da7e-403e-9eb5-bf4b4d40522a
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "9.10-64 on sda14 (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set d4e5d7ce-da7e-403e-9eb5-bf4b4d40522a
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "10.04-64 on sda16 (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set d4e5d7ce-da7e-403e-9eb5-bf4b4d40522a
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Sid on sda6 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sda6 ro quiet
    initrd /initrd.img
}
menuentry "Squeeze on sda8 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sda8 ro quiet
    initrd /initrd.img
}
menuentry "10.04-32 on sda10 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda8 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sda8 ro quiet
    initrd /initrd.img
}
menuentry "9.10-64 on sda14 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "10.04-64 on sda16 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sdb10 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb10 ro quiet
    initrd /initrd.img
}
menuentry "Lounge on sdb7 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb7 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sdb13 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb13 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sdb15 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb15 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sdb12 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb12 ro quiet
    initrd /initrd.img
}
menuentry "Xmonad on sdb14 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb14 ro quiet
    initrd /initrd.img
}
menuentry "Stoner1.2 on sdb16 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb16 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sdb11 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb11 ro quiet
    initrd /initrd.img
}
menuentry "Zenix on sdb9 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb9 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sdb6 (on /dev/sda14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos14)'
    search --no-floppy --fs-uuid --set 4324e46e-b9e8-4edc-ad46-286b54469535
    linux /vmlinuz root=/dev/sdb6 ro quiet splash
    initrd /initrd.img
}
menuentry "Sid on sda6 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1387a9b7-0844-4ab7-a4b1-a32e050bb26c
    linux /vmlinuz root=/dev/sda6 ro quiet
    initrd /initrd.img
}
menuentry "Sqeeze on sda8 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1387a9b7-0844-4ab7-a4b1-a32e050bb26c
    linux /vmlinuz root=/dev/sda8 ro quiet
    initrd /initrd.img
}
menuentry "10.04-32 on sda10 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1387a9b7-0844-4ab7-a4b1-a32e050bb26c
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "9.04-64 on sda12 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1387a9b7-0844-4ab7-a4b1-a32e050bb26c
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "9.10-64 on sda14 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1387a9b7-0844-4ab7-a4b1-a32e050bb26c
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "10.04-64 on sda16 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1387a9b7-0844-4ab7-a4b1-a32e050bb26c
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Plymouth on sda6 (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set db535c87-e88b-4391-ad2e-962468f0fb4e
    linux /vmlinuz root=/dev/sda6 ro quiet
    initrd /initrd.img
}
menuentry "Sqeeze on sda8 (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set db535c87-e88b-4391-ad2e-962468f0fb4e
    linux /vmlinuz root=/dev/sda8 ro quiet
    initrd /initrd.img
}
menuentry "10.04-32 on sda10 (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set db535c87-e88b-4391-ad2e-962468f0fb4e
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "9.04-64 on sda12 (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set db535c87-e88b-4391-ad2e-962468f0fb4e
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "9.10-64 on sda14 (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set db535c87-e88b-4391-ad2e-962468f0fb4e
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "10.04-64 on sda16 (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set db535c87-e88b-4391-ad2e-962468f0fb4e
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda10 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda7 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sda13 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda13 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sda15 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda15 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sda12 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda12 ro quiet
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda16 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda11 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda11 ro quiet
    initrd /initrd.img
}
menuentry "Lizard on sda9 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda9 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro quiet splash
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (recovery mode) (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro single
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-18-generic (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-18-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro quiet splash
    initrd /boot/initrd.img-2.6.35-18-generic
}
menuentry "Ubuntu, with Linux 2.6.35-18-generic (recovery mode) (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-18-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro single
    initrd /boot/initrd.img-2.6.35-18-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro quiet splash
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (recovery mode) (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro single
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro quiet splash
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (recovery mode) (on /dev/sdb10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos10)'
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro single
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Stoner1.2 on sda1 (on /dev/sdb11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos11)'
    search --no-floppy --fs-uuid --set 4e3a2c05-e455-4c21-bbe7-6ed13e480811
    linux /vmlinuz root=/dev/sda1 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda2 (on /dev/sdb11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos11)'
    search --no-floppy --fs-uuid --set 4e3a2c05-e455-4c21-bbe7-6ed13e480811
    linux /vmlinuz root=/dev/sda2 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda3 (on /dev/sdb11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos11)'
    search --no-floppy --fs-uuid --set 4e3a2c05-e455-4c21-bbe7-6ed13e480811
    linux /vmlinuz root=/dev/sda3 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda4 (on /dev/sdb11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos11)'
    search --no-floppy --fs-uuid --set 4e3a2c05-e455-4c21-bbe7-6ed13e480811
    linux /vmlinuz root=/dev/sda4 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda10 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda7 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sda13 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda13 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sda15 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda15 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sda12 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda12 ro quiet
    initrd /initrd.img
}
menuentry "Xmonad on sda14 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda16 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda11 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda11 ro quiet
    initrd /initrd.img
}
menuentry "Zenix on sda9 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda9 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sdb12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos12)'
    search --no-floppy --fs-uuid --set ca029efe-a9c7-4d39-93da-ed081d1380e7
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda7 ro quiet
    initrd /initrd.img
}
menuentry "StonedLizard on sda11 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda11 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sda14 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sda16 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda16 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sda13 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda13 ro quiet
    initrd /initrd.img
}
menuentry "Xmonad on sda15 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda15 ro quiet
    initrd /initrd.img
}
menuentry "Lubuntu on sda12 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda12 ro quiet
    initrd /initrd.img
}
menuentry "Zenix on sda10 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda10 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda8 (on /dev/sdb13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos13)'
    search --no-floppy --fs-uuid --set 597781ef-23ad-4bc5-8b44-c9fe25464d85
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda10 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda7 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sda13 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda13 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sda15 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda15 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sda12 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda12 ro quiet
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda16 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda11 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda11 ro quiet
    initrd /initrd.img
}
menuentry "Lizard on sda9 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda9 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Zenix, Linux 2.6.31-14-generic (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6d4963cf-a4be-4c36-a017-cade3e1071b6 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Zenix, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos14)'
    search --no-floppy --fs-uuid --set 6d4963cf-a4be-4c36-a017-cade3e1071b6
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6d4963cf-a4be-4c36-a017-cade3e1071b6 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Lounge on sda7 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda7 ro quiet
    initrd /initrd.img
}
menuentry "StonedLizard on sda11 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda11 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sda14 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sda16 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda16 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sda13 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda13 ro quiet
    initrd /initrd.img
}
menuentry "Xmonad on sda15 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda15 ro quiet
    initrd /initrd.img
}
menuentry "Lubuntu on sda12 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda12 ro quiet
    initrd /initrd.img
}
menuentry "Zenix on sda10 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda10 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda8 (on /dev/sdb15)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos15)'
    search --no-floppy --fs-uuid --set ca243492-46b4-412f-8bd4-5c239a4f151c
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda1 (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /vmlinuz root=/dev/sda1 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda2 (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /vmlinuz root=/dev/sda2 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda3 (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /vmlinuz root=/dev/sda3 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda4 (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /vmlinuz root=/dev/sda4 ro quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro quiet splash
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (recovery mode) (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro single
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-18-generic (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-18-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro quiet splash
    initrd /boot/initrd.img-2.6.35-18-generic
}
menuentry "Ubuntu, with Linux 2.6.35-18-generic (recovery mode) (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-18-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro single
    initrd /boot/initrd.img-2.6.35-18-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro quiet splash
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (recovery mode) (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro single
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro quiet splash
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (recovery mode) (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro single
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Ubuntu, with Linux 2.6.35-15-generic (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-15-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro quiet splash
    initrd /boot/initrd.img-2.6.35-15-generic
}
menuentry "Ubuntu, with Linux 2.6.35-15-generic (recovery mode) (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-15-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro single
    initrd /boot/initrd.img-2.6.35-15-generic
}
menuentry "Ubuntu, with Linux 2.6.35-14-generic (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-14-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro quiet splash
    initrd /boot/initrd.img-2.6.35-14-generic
}
menuentry "Ubuntu, with Linux 2.6.35-14-generic (recovery mode) (on /dev/sdb16)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos16)'
    search --no-floppy --fs-uuid --set d10d3594-cca1-4dae-b7c1-3c57c1952acc
    linux /boot/vmlinuz-2.6.35-14-generic root=UUID=d10d3594-cca1-4dae-b7c1-3c57c1952acc ro single
    initrd /boot/initrd.img-2.6.35-14-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-28-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-28-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-28-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
    initrd /boot/initrd.img-2.6.24-28-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-27-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-27-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
    initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-26-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-26-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
    initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/memtest86+.bin 
}
menuentry "Lounge on sda7 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda7 ro quiet
    initrd /initrd.img
}
menuentry "StonedLizard on sda11 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda11 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sda14 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda14 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sda16 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda16 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sda13 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda13 ro quiet
    initrd /initrd.img
}
menuentry "Xmonad on sda15 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda15 ro quiet
    initrd /initrd.img
}
menuentry "Lubuntu on sda12 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda12 ro quiet
    initrd /initrd.img
}
menuentry "Zenix on sda10 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda10 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda8 (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-18-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-18-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.35-18-generic
}
menuentry "Ubuntu, with Linux 2.6.35-18-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-18-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.35-18-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Ubuntu, with Linux 2.6.35-15-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-15-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.35-15-generic
}
menuentry "Ubuntu, with Linux 2.6.35-15-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-15-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.35-15-generic
}
menuentry "Ubuntu, with Linux 2.6.35-14-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-14-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.35-14-generic
}
menuentry "Ubuntu, with Linux 2.6.35-14-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.35-14-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.35-14-generic
}
menuentry "StonedLizard on sda10 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda10 ro quiet
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda7 ro quiet
    initrd /initrd.img
}
menuentry "Mangey Moose on sda13 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda13 ro quiet
    initrd /initrd.img
}
menuentry "Adding Gnome on sda15 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda15 ro quiet
    initrd /initrd.img
}
menuentry "ISO-test on sda12 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda12 ro quiet
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda16 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda11 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda11 ro quiet
    initrd /initrd.img
}
menuentry "Lizard on sda9 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda9 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sdb9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set fd3ccc06-b103-428f-97dd-d3105bc99351
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```
So, to straighten this out all I need to do is **** around booting through this crap or use the live CD to recover my second internals ability to boot on its own and then straighten out grub in this new install so that I can try it on the external.

This is not an improvement over having the ability to simply tell it not to install grub.  This just sucks in a big way.

I do not think that folks who get a second drive to install on, thinking this will avoid problems  will be very happy with this.

True, it does not appear to have installed on any partitions.  This should save MS users Boot Sectors.

This over simplification to make it "easy" for idiots is just a really disgusting bunch of crap that is not going to work as the idiots will get screwed anyway.

---

### Post by kansasnoob on 2010-08-28
> **cariboo907 said:**
> I did an install from todays daily live, aside form not giving you a choice of where to install grub, **[COLOR="Red"]there isn't an option to change your computer name[/COLOR]**, with 8 systems in use, it a lot easier to keep track of them by name than it by ip address.

I found another couple of oddities, when you first get the screen that gives you a choice whether to install or try, the indicator-applet-session and sound icons were on the left side of the upper panel. Some of the installation screens are the right size, but once you get to the actual install you have to use the scroll bar to see the contents of the window.

The one good thing about there being no choice on where to put grub, at least new users can't accidentally install it on their Windows partition. Grub found all my partitions and listed them in the menu with no problem.

That's a great point! I hadn't thought about that but that's particularly problematic since they changed the Sys > Admin > Networking gui. It can now be somewhat of a kludge changing the computer name.

I tried searching for a ubiquity bug regarding that with no luck. That'd be a good one to file :)

I hope to review existing ubiquity bugs just before iso-testing so I can somewhat quickly file bugs as I test. With the beta due on Sept 2 I'd expect iso-testing to begin either Monday or Tuesday.

I'd appreciate knowing what all existing bugs have been reported to save time :D

Of course I know about the one in post #1 of this thread, the rest listed in post #29 appear to have been fixed, so what still needs to be reported:

No way to select computer name?

No way to maximize or resize installer windows?

What am I not thinking of?

---

### Post by cariboo on 2010-08-28
It's fairly easy to change the host name by hand, but I don't expect a new user would find it easy. My reasoning is that with several computers running Ubuntu all of the systems use the same hostnames:

```
<user>-desktop
```

This can lead to confusion (at least for me). I regularly log into different computers on my network via ssh seeing:

cariboo@willy or cariboo@puntzi makes a lot more sense than seeing cariboo@cariboo-desktop when logging in.

I also use different hostnames for different installations, the system I'm using now has a hostname of:

```
cariboo@alexis-maverick:~$
```

This tells me that I'm logged into my system at home and it's running maverick. the other partition running lucid has the hostname:

```
cariboo@alexis:~$
```

The way ubiquity is now, it would be perfect for a new user with a single computer with only Windows and Ubuntu installed, but how about the rest of use that have different setups?

---

### Post by kansasnoob on 2010-08-28
> **cariboo907 said:**
> It's fairly easy to change the host name by hand, but I don't expect a new user would find it easy. My reasoning is that with several computers running Ubuntu all of the systems use the same hostnames:

```
<user>-desktop
```

This can lead to confusion (at least for me). I regularly log into different computers on my network via ssh seeing:

cariboo@willy or cariboo@puntzi makes a lot more sense than seeing cariboo@cariboo-desktop when logging in.

I also use different hostnames for different installations, the system I'm using now has a hostname of:

```
cariboo@alexis-maverick:~$
```

This tells me that I'm logged into my system at home and it's running maverick. the other partition running lucid has the hostname:

```
cariboo@alexis:~$
```

The way ubiquity is now, it would be perfect for a new user with a single computer with only Windows and Ubuntu installed, but how about the rest of use that have different setups?

Well, the old way (I think up through Hardy or Intrepid) you could just change with a gui. I think in Jaunty you could just do "gedit /etc/hostname", but by Karmic things got more complicated.

Regardless the option to "name" the puter should be available during installation!

I normally don't test the alternate but I might this time after completing my testing with the Live CD, just in case. I have not tried an alternate since 10.04 was first released, and I only did that to be sure I still understood how it worked :)

---

### Post by cariboo on 2010-08-28
The alternate still uses the debian installer, so all the normal options are still there. 

The one extra I did notice using the daily live, is now there is an opportunity to encrypt the home directory, whereas that option was only on the alternate before.

---

### Post by kansasnoob on 2010-08-31
It looks like this might be fixed now:

> ubiquity (2.3.10) maverick; urgency=low

  [ Evan Dandrea ]
  * Handle crashes in parallel debconffilters by failing the
    installation.
  * [B][COLOR="Red"]Add a grub target device combobox on the GTK and KDE advanced
    partitioning pages.[/COLOR][/B]
  * Bootloader handling is now done in ubi-partman.  Do not overwrite it
    with the default selection in plugininstall.
  * Get rid of the quitting state variable and use the existing
    current_page construct (LP: #627284).

  [ Mario Limonciello ]
  * Add a new script that uses python-aptdaemon-gtk for oem-config removal.
  * If running with only installable languages, don't offer "No Localization"
  * If only one language is available, mark the language page as complete.
 -- Evan Dandrea <evand@ubuntu.com>   Tue, 31 Aug 2010 12:19:00 +0100

I'll know more as soon as they get the Ubuntu i386 image up for iso-testing :)

AFAIK only two issues remain:

1) Installer screen can't be resized.
2) No option to change "computer-name".

---

### Post by VMC on 2010-08-31
> **kansasnoob said:**
> It looks like this might be fixed now:



I'll know more as soon as they get the Ubuntu i386 image up for iso-testing :)

AFAIK only two issues remain:

1) Installer screen can't be resized.
2) No option to change "computer-name".
I don't know where you got your quote, but today's iso didn't have that change yet. At least the zsync that I just did. I'll have to check what ubiquity version it has.

---

### Post by cariboo on 2010-08-31
It seems the partitioner has changed again too, It seems there were more choices with last weeks daily build. I did do a successful vbox install with todays live image. I'll post a screen shot a little later.

**Edit**: I guess I was wrong, there still is the same choices/

---

### Post by kansasnoob on 2010-08-31
> **VMC said:**
> I don't know where you got your quote, but today's iso didn't have that change yet. At least the zsync that I just did. I'll have to check what ubiquity version it has.

That's the changelog for 'ubiquity (2.3.10) maverick':

[https://launchpad.net/ubuntu/maverick/+source/ubiquity/2.3.10](https://launchpad.net/ubuntu/maverick/+source/ubiquity/2.3.10)

I'm waiting for the official Ubuntu i386 iso-testing build before I zsync again, and I'm just finishing up my upgrade test :)

---

### Post by kansasnoob on 2010-08-31
> **cariboo907 said:**
> It seems the partitioner has changed again too, It seems there were more choices with last weeks daily build. I did do a successful vbox install with todays live image. I'll post a screen shot a little later.

**Edit**: I guess I was wrong, there still is the same choices/

Cool, I'd love if you could tell me how you attached three screenshots in one attachment. I see it calls them 'thumbnails' but that's an awesome trick :)

I've occasionally wanted to attach more than 2 or 3 images (because sometimes a picture truly is worth a thousand words) and had to use two or more posts.

BTW I know the debian-installer is not related to ubiquity but I use it so seldom I thought it would be smart to give it a whirl and look for any bugs :)

---

### Post by kansasnoob on 2010-08-31
Hat Tip to Evan Dandrea:

> ubiquity (2.3.12) maverick; urgency=low

  * Argh.  Missing import.
 -- Evan Dandrea <evand@ubuntu.com>   Tue, 31 Aug 2010 21:31:02 +0100

I've had the pleasure of working with Evan before, with myself on the testing end, and he's a pleasant and courteous person. When I go back to this:

> [ Evan Dandrea ]
* **[COLOR="Red"]Merge maverick-redesign branch. Fingers crossed.[/COLOR]**
* Automatic update of included source packages: clock-setup
0.103ubuntu1.

-- Evan Dandrea <evand@ubuntu.com> Fri, 06 Aug 2010 14:15:17 -0400 

Full quote here:

[http://ubuntuforums.org/showpost.php?p=9698660&postcount=14](http://ubuntuforums.org/showpost.php?p=9698660&postcount=14)

Evan knew he was in for a heck of a ride but he's hanging in and getting this done!

We should all respect that kind of commitment :D

---

### Post by cariboo on 2010-08-31
> **kansasnoob said:**
> Cool, I'd love if you could tell me how you attached three screenshots in one attachment. I see it calls them 'thumbnails' but that's an awesome trick :)

I've occasionally wanted to attach more than 2 or 3 images (because sometimes a picture truly is worth a thousand words) and had to use two or more posts.

BTW I know the debian-installer is not related to ubiquity but I use it so seldom I thought it would be smart to give it a whirl and look for any bugs :)

If you go to the advanced editor, scroll down until you see a Manage Attachments button. click it and you should see the Manage Attachment form come up, it's pretty self explanitory from there. See screenshot.

---

### Post by DanaG on 2010-09-02
> **cariboo907 said:**
> ... I also use different hostnames for different installations... 

Handy trick: create a file /etc/debian_chroot, and put some label in it.  For example:
```
(maverick)[COLOR="Lime"]dana@EliteBook[/COLOR]:[COLOR="Blue"]~[/COLOR]$ sudo chroot /media/hdd-root/
[sudo] password for dana: 
(lucid)[COLOR="Lime"]root@EliteBook[/COLOR]:[COLOR="Blue"]/[/COLOR]# 
```

I also have copied the SSH host key between the two partitions, so I don't get inconsistencies.

---

### Post by 67GTA on 2010-09-02
I noticed the daily build from the 1st has the grub install option on the manual install screen. I guess it is just hidden on the guided install.

---

### Post by kansasnoob on 2010-09-02
I just commented on the original bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033)

> 

I believe you'll find this was fixed in ubiquity 2.3.10, however that option will only be available while using the advanced/manual partitioner:

ubiquity (2.3.10) maverick; urgency=low

[ Evan Dandrea ]
* Handle crashes in parallel debconffilters by failing the
installation.
* Add a grub target device combobox on the GTK and KDE advanced
partitioning pages.
* Bootloader handling is now done in ubi-partman. Do not overwrite it
with the default selection in plugininstall.
* Get rid of the quitting state variable and use the existing
current_page construct (LP: #627284).

[ Mario Limonciello ]
* Add a new script that uses python-aptdaemon-gtk for oem-config removal.
* If running with only installable languages, don't offer "No Localization"
* If only one language is available, mark the language page as complete.
-- Evan Dandrea <evand@ubuntu.com> Tue, 31 Aug 2010 12:19:00 +0100


Very quickly I was asked:

> Thanks Erick that's what we were looking for. One question though. **[COLOR="Red"]What if you don't want to install the boot loader.[/COLOR]** For example if your running multiple Linux distros and you don't what the current boot loader to be over written?

So I had to spin up the live CD and have a look. I see no option to NOT install grub like before where you could just uncheck a box, but I stumbled onto two options I don't understand:

/dev/sda-1
/dev/sdb-1

NO TYPOS! Look:

[ATTACH]168341[/ATTACH]

Does anyone know what those designations mean with a "-"? I've never seen that before :D

I really need to try and figure out how to use IRC chat so I can connect to #grub but with my poor visual accuity it's always boggled my mind :confused:

Just so everyone can get a better mental picture of my drive/partition layout:

```
lance@lance-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+  83  Linux
/dev/sda2            2611        5219    20956792+  83  Linux
/dev/sda3            5220       18363   105579180   83  Linux
/dev/sda4           18364       60801   340883173    5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux
/dev/sda13          28691       31365    21486906   83  Linux
/dev/sda14          18364       20924    20571169+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000d7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2672    21453824   83  Linux
/dev/sdb2            2672        9730    56695808    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

```

And blkid w/labels:

```
lance@lance-desktop:~$ sudo blkid
/dev/sda1: LABEL="Maverick" UUID="b7a0df33-53e4-4f0d-856b-0da92ff0d743" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda10: LABEL="Isadora" UUID="f223fe5d-3acb-4d96-950c-62661ad8714b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Squeeze" UUID="0eec2831-7805-437e-a06e-e18ab3268e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="Pure Gnome" UUID="f6062e12-09f1-4f19-b6c2-ad58812d6794" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="Peppermint" UUID="720d719e-e571-4bdd-aac9-718f0ffe2266" TYPE="ext4" 
/dev/sda14: LABEL="LL to MM test" UUID="c703501f-1f50-465f-8eb7-9f20cbd3485a" TYPE="ext4" 
/dev/sda2: LABEL="Karmic" UUID="1332b9d0-cf18-4299-9094-12acbdac91ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Lucid" UUID="d252929b-949d-432e-a18c-18f9ae770d28" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="80627269-1ccd-4774-b4ea-a5ef8824ffaa" TYPE="swap" 
/dev/sdb5: UUID="5a66ab05-104c-4625-9429-6d143d2519b6" TYPE="swap" 
/dev/sdb1: LABEL="Maverick Test" UUID="3f034d3f-00f4-437c-9514-febbcd52c407" TYPE="ext4" 

```

One additional thing I thought of is that I have two VM's in Lucid on sda3 that I was using for testing the new ubiquity in both Ubuntu and Kubuntu. I think I'll delete them and spin up the Live CD again to have a fresh look.

One would hope it's not offering virtual discs as grub-install devices :p

---

### Post by ronacc on 2010-09-02
swap partitions ?

---

### Post by kansasnoob on 2010-09-03
> **ronacc said:**
> swap partitions ?

I'd hope not :p

And, if so, why not just use actual partition #'s?

I've never seen a "-" used in any Linux drive/partition designation.

If we don't have an answer in a couple of days I'll subscribe Colin Watson to that bug and see what he says.

It would be better if someone that uses IRC chat could hook into #grub and ask :D

I should figure out how to do that but I'm visually impaired and that's never been a priority.

---

### Post by ktp on 2010-09-03
it is interesting...never seen that before either.  You got me wondering now. =)

---

### Post by ktp on 2010-09-03
> **kansasnoob said:**
> I've never seen a "-" used in any Linux drive/partition designation.


It seems it has happened in the past, the "sda-1", but still no idea what it is for:

[http://ubuntuforums.org/showthread.php?t=1497330](http://ubuntuforums.org/showthread.php?t=1497330)

---

### Post by VMC on 2010-09-03
> **kansasnoob said:**
> I just commented on the original bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033)



Very quickly I was asked:



So I had to spin up the live CD and have a look. I see no option to NOT install grub like before where you could just uncheck a box, but I stumbled onto two options I don't understand:

/dev/sda-1
/dev/sdb-1

NO TYPOS! Look:

[ATTACH]168341[/ATTACH]

Does anyone know what those designations mean with a "-"? I've never seen that before :D

I really need to try and figure out how to use IRC chat so I can connect to #grub but with my poor visual accuity it's always boggled my mind :confused:
Yes, sometimes I don't won't the current install to touch the bootloader for various reasons.
Maybe the "-1" are a glitch and should be just sda1/sdb1

---

### Post by kansasnoob on 2010-09-03
> **VMC said:**
> Yes, sometimes I don't won't the current install to touch the bootloader for various reasons.
Maybe the "-1" are a glitch and should be just sda1/sdb1

But those are both already listed.

I'm sure Colin Watson could tell us because be works on both grub and ubiquity.

I don't use IRC chat but I think he's on #grub.

If we don't have an answer in a couple of days I'll subscribe him to the bug report.

---

### Post by VMC on 2010-09-03
> **kansasnoob said:**
> But those are both already listed.

I'm sure Colin Watson could tell us because be works on both grub and ubiquity.

I don't use IRC chat but I think he's on #grub.

If we don't have an answer in a couple of days I'll subscribe him to the bug report.
Then maybe they refer to writing grub to the partition instead of the MBR of that partition, hence the "-1"

---

### Post by ranch hand on 2010-09-03
You have done a lot of installs recently.  Do another.  Install on sda-1.  What is the worst that can happen?

Well ok, so you installed grub in place of your bios, who uses that crap anyway.

I would really like to know what that is, but I know that I am not going to attempt to install grub on something that I do not recognize.

It could, long shot, be an null command and using it will install grub no where.   May be wishful thinking.

If it is you have to admit that it is much easier to understand than just not selecting anything and getting on with life.  It is intuitive.

---

### Post by vishalrao on 2010-09-03
I dont see the -1, just the expected /dev/sda and /dev/sda1, /dev/sda2 etc...

Kubuntu's installer allows you to set hostname but just like ubuntu's doesn't allow you to not install grub.

---

### Post by VMC on 2010-09-03
> **vishalrao said:**
> I dont see the -1, just the expected /dev/sda and /dev/sda1, /dev/sda2 etc...

Kubuntu's installer allows you to set hostname but just like ubuntu's doesn't allow you to not install grub.

I just installed the beta on another partition , I don't see the "-1" either. I wonder if Kansas has another hard drive. I only have one.

---

### Post by ronparent on 2010-09-03
I admit I worried about the lack of a grub option on the new installer. I was installing to a raid0 partition and had cause for concern. The installation was flawless and the grub boot loader ended up where it belonged - on the boot drive, the raid! This was a first. Good work by the developers.

---

### Post by kansasnoob on 2010-09-03
I added some machine info to post #63:

[http://ubuntuforums.org/showpost.php?p=9799501&postcount=63](http://ubuntuforums.org/showpost.php?p=9799501&postcount=63)

I'm going to delete the two virtual discs in sda3 and see if that changes things.

---

### Post by kansasnoob on 2010-09-03
Well, it wasn't the VM's :)

---

### Post by vishalrao on 2010-09-04
I've got two disks, perhaps its messed-up partition tables or a pre-beta cd image?

---

### Post by AClark on 2010-09-04
I just had occasion to reinstall 10.04 after a hard disk failure.  Installed 10.04.1 64bit zsynched with the daily live desktop as of two or three days ago.  On the advanced tab I had all my partitions available plus sda-1 and sdb-1.  

sdc was mounted and there was no sdc-1

It would make sense (sort of) if the -1 denoted don't install.

If it hadn't been so late and I had a little more ambition I would have tried one of those choices just to see what happened.  I'm surprised one of you guys hasn't.

---

### Post by kansasnoob on 2010-09-04
> **AClark said:**
> I just had occasion to reinstall 10.04 after a hard disk failure.  Installed 10.04.1 64bit zsynched with the daily live desktop as of two or three days ago.  On the advanced tab I had all my partitions available plus sda-1 and sdb-1.  

sdc was mounted and there was no sdc-1

It would make sense (sort of) if the -1 denoted don't install.

If it hadn't been so late and I had a little more ambition I would have tried one of those choices just to see what happened.  I'm surprised one of you guys hasn't.

So, you were using a 10.04.1 disc? While that would have nothing to do with 10.10 that's interesting.

I have a 10.04.1 disc here since I did testing for it so I'll check it out.

I've just not been able to find any info about drive/partition designations with a "-" as shown in mine.

---

### Post by kansasnoob on 2010-09-04
> **AClark said:**
> I just had occasion to reinstall 10.04 after a hard disk failure.  Installed 10.04.1 64bit zsynched with the daily live desktop as of two or three days ago.  On the advanced tab I had all my partitions available plus sda-1 and sdb-1.  

sdc was mounted and there was no sdc-1

It would make sense (sort of) if the -1 denoted don't install.

If it hadn't been so late and I had a little more ambition I would have tried one of those choices just to see what happened.  I'm surprised one of you guys hasn't.

IOU big time! You're so right:

[ATTACH]168512[/ATTACH]

So this is a grub-pc thing rather than a ubiquity thing.

I seriously owe you big! Should you ever end up in Marion, KS I'll buy you the meal of your choice. If you're smart you'll go for pizza at Gambino's. Anything else may leave you with a bad case of travelers :D

Seriously, I owe you big time :D

I'll pour over recent grub-pc changelogs now and see if I can find an explanation.

---

### Post by VMC on 2010-09-04
> **AClark said:**
> I just had occasion to reinstall 10.04 after a hard disk failure.  Installed 10.04.1 64bit zsynched with the daily live desktop as of two or three days ago.  On the advanced tab I had all my partitions available plus sda-1 and sdb-1.  

sdc was mounted and there was no sdc-1

It would make sense (sort of) if the -1 denoted don't install.

If it hadn't been so late and I had a little more ambition I would have tried one of those choices just to see what happened.  I'm surprised one of you guys hasn't.

This would make since if we all had the "-1". I don't.
I booted using LiveUSB and one internet hard drive. It shows both usb and hard drive but no "-1" anywhere.

---

### Post by AClark on 2010-09-04
I've been following this thread (and several others) with interest - 

I realize this is the 10.10 forum but I haven't done an install of 10.10 since this thread started and when I stumbled on this while installing 10.04 I was pretty sure you would be interested.

> Should you ever end up in Marion, KS I'll buy you the meal of your choice

I'd love to take you up on that but not likely.  I've only been west of the Mississippi once and the older I get the less I'm inclined to travel off the farm.

Looking forward to the answer to this puzzlement.

---

### Post by ronacc on 2010-09-05
I just installed the beta to a box with 3 HD's and an ssd , and several partitions , all partitions showed in the partitioner but no -1's .

---

### Post by cariboo on 2010-09-05
I'll add my +1 to the rest, 2 hdd 6 partitions no -1's

---

### Post by ktp on 2010-09-05
this -1 thing is killing me...I knew it happened in lucid because of this post: 

[http://ubuntuforums.org/showthread.php?t=1497330](http://ubuntuforums.org/showthread.php?t=1497330)

But I can't seem to find what is doing it and why. If someone finds out more please share (am sure you will but just saying =) ).

---

### Post by kansasnoob on 2010-09-06
Still no answer here :(

Thought it was time for a bump. I have been asking around.

If I'm left with no other option I'll try subscribing Colin Watson to that bug report. I know he'll be able to tell us.

And, NO, I will not just randomly try installing to a device that I don't understand!

I doubt it would hose my BIOS but I never do anything without knowing what I'm getting into.

---

### Post by VMC on 2010-09-06
> **kansasnoob said:**
> ...
And, NO, I will not just randomly try installing to a device that I don't understand!

I doubt it would hose my BIOS but I never do anything without knowing what I'm getting into.

What are you talking about. You use Maverick testing, and we never know what we get from day to day.

---

### Post by AClark on 2010-09-06
> And, NO, I will not just randomly try installing to a device that I don't understand!

Where's the fun in that !

Seriously - I have enough junk computers around - If I can find the time I intend to see what happens. Unless someone comes up with the answer before I do.

However my brothers and I are apple growers and we are just starting harvest so I won't have much or any spare time for the next three months.

---

### Post by ranch hand on 2010-09-06
> **AClark said:**
> Where's the fun in that !

Seriously - I have enough junk computers around - If I can find the time I intend to see what happens. Unless someone comes up with the answer before I do.

However my brothers and I are apple growers and we are just starting harvest so I won't have much or any spare time for the next three months.
Completely off Topic but I worked for an orchard back in Ohio a long time ago.  Liked it a lot.  Still fool with trees if I get the chance.

Hope the picking goes well.

---

### Post by ktp on 2010-09-06
> **kansasnoob said:**
> Still no answer here :(

Thought it was time for a bump. I have been asking around.

If I'm left with no other option I'll try subscribing Colin Watson to that bug report. I know he'll be able to tell us.

And, NO, I will not just randomly try installing to a device that I don't understand!

I doubt it would hose my BIOS but I never do anything without knowing what I'm getting into.

are you using mac?  The only pattern I have seen is lots of people with mac see this.

---

### Post by ktp on 2010-09-06
> **AClark said:**
> Where's the fun in that !

Seriously - I have enough junk computers around - If I can find the time I intend to see what happens. Unless someone comes up with the answer before I do.

However my brothers and I are apple growers and we are just starting harvest so I won't have much or any spare time for the next three months.

if you do, I am really interested into knowing what happens.  But real work before fun. =)

---

### Post by VMC on 2010-09-06
> **ktp said:**
> if you do, I am really interested into knowing what happens.  But real work before fun. =)

If your referring to the infamous "-1", I would love to try it. I never see it! If ever I see the "-1" again, that's where gruby is going for sure.

---

### Post by ktp on 2010-09-06
> **VMC said:**
> If your referring to the infamous "-1", I would love to try it. I never see it! If ever I see the "-1" again, that's where gruby is going for sure.

yep that is what i am talking about.  I have not seen it yet, but really interested into knowing more.

---

### Post by AClark on 2010-09-06
> **ktp said:**
> are you using mac?  The only pattern I have seen is lots of people with mac see this.

Nothing but pure Ubuntu (PC) here.

Two SATA drives - one data only - one with prior Ubuntu installs - option showed up for sda-1 and sdb-1

I may be dense but I don't see a pattern.

---

### Post by ktp on 2010-09-06
thanks...i can't see a pattern either now.  I have similar setup to yours and I don't see "-1".

---

