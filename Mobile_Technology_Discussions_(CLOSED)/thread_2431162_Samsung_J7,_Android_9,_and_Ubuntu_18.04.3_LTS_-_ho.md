---
title: "Samsung J7, Android 9, and Ubuntu 18.04.3 LTS - how to connect?"
date: 2019-11-12
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Bartender on 2019-11-12
Sorry if this has been answered.  I'm trying to access photos and other files on a new Samsung J7 running Android 9.  I have two identical HP 8300 SFF PC's setting next to each other; one's running Windows 10 and the other is Ubuntu 18.04.3.

Using the cable that came with the Samsung, the phone connects to the Windows PC.  I can see the files.  Thumbnails of the pictures appear.  So the cable appears to be OK.  When I plug it in, a window pops up on the phone asking if I want to allow file transfer, "Allow" or "Deny".  I tap "Allow" and Windows File Explorer opens the phone.  That's using one of the USB ports on the front of the PC, which in my limited experience is less reliable than the ports on the back.

OK, over to the Ubuntu PC. Using the same cable, plugged into the front or back of the PC, the phone pops up with the same message, "Allow" or "Deny".  I tap on "Allow".  Nautilus window pops up, it shows the Samsung, but the wheel just keeps on spinning and spinning.

"Android File Transfer" seems like a valid thing to try.  It looks like there are some ideas for transferring wirelessly too?

---

### Post by Redalien0304 on 2019-11-12
would this help from omgubuntu
[h=1][SIZE=1]How to Mirror & Control Your Android Phone from the Ubuntu Desktop[/SIZE][/h][https://www.omgubuntu.co.uk/2019/07/scrcpy-mirror-android-to-ubuntu-linux](https://www.omgubuntu.co.uk/2019/07/scrcpy-mirror-android-to-ubuntu-linux)

---

### Post by Bartender on 2019-11-12
Off to a bad start - the instructions discuss how to enable developer options.  Says (To Enable developer options in Android is easy: just reputedly tap the build/version number listed in Settings > System > About Phone)

That didn't work.  Wait a minute.  Not "reputedly" - repeatedly.  I tapped on Build number several times.  A little window popped up saying developer options was now turned on.  Just for the heck of it I tried plugging the phone in.  Same as before.  The wheel just spins.  

I installed "Developer Tools", the first app that popped up in Google Play Store when I searched for developer.  Found the USB debugging mode.  Turned it to "On".  Restarted phone.  Still nothing in Nautilus.

Installed scrcpy using the link in that article.  Started from terminal.

scrcpy
INFO: scrcpy 1.10 <https://github.com/Genymobile/scrcpy>
adb: error: failed to get feature set: device unauthorized.
This adb server's $ADB_VENDOR_KEYS is not set
Try 'adb kill-server' if that seems wrong.
Otherwise check for a confirmation dialog on your device.
ERROR: "adb push" returned with value 1

I don't care about adb.  Using USB.  Nothing seems to happen.
Nautilus still can't open the phone. Wheel just spins.

OK weird I turned phone off, turned it back on tried again now scrcpy works!  Just like it said.  Started scrcpy from terminal

scrcpy
INFO: scrcpy 1.10 <https://github.com/Genymobile/scrcpy>
/usr/local/share/scrcpy/scrcpy-server....shed. 1.6 MB/s (22546 bytes in 0.013s)
INFO: Initial texture: 720x1280

Got this message, and a second or two later a window popped up that looks just like the phone.  The mouse made things happen.  Trippy.  

However, this doesn't really get me where I wanted to go.  Nautilus still doesn't see the phone's data.  I just wanted to transfer pictures & video to the Ubuntu PC.

---

### Post by coffeecat on 2019-11-13
This isn't going to help you much, but I can tell you that plugging an Android 9 phone into Ubuntu 18.04 *should* just work. With my Android 9 Nokia smartphone, I get the allow/deny popup on the phone, and also a Nautilus window that doesn't show the contents of the phone. After I tap allow on the phone, a second Nautilus window appears in which I can browse the contents of the phone, read-write. With an older Motorola phone running Android 6, I had to enable developer options, but that's not been necessary since I replaced it with the Nokia, originally running Android 7. I have since purchased a couple more different model Nokias (long story!), and they and Ubuntu 18.04 get along just fine.

From your description, it sounds as though your Ubuntu system is trying to display the second Nautilus instance, but failing. 

In the past I thought that the version of Android was the issue, but there was a thread on the forum about a similar problem a couple of years ago where it became apparent that different people running the same version of Android on different makes of phones were getting different things. Which makes me think that something Samsung have done might be causing the problem in your case. I know that doesn't help much, except it might provide a clue in your google searches.

"Reputedly" - how irritating! :) Yes, it's repeatedly, 7 times to be precise.

---

### Post by Bartender on 2019-11-13
Hi, coffeecat -
Thanks for taking the time.  When I first read those instructions, I thought the author used the word "reputedly" because he'd heard about it but hadn't tried it.  I finally hit the button a couple of times, out of frustration as much as anything else, and a little window popped up saying "You're five taps away from enabling developer options" or something like that.
About 3 years ago, with my first smartphone (Samsung J3), plugging it into whatever flavor Ubuntu I was running at the time "just worked" so it was discouraging to run into trouble now.  It does help to hear someone say that their mobile device worked with 18.04.  
It also helps that the same phone and cable works with the Windows PC.

So I tried it again this morning.
Just picked the phone up and plugged it into the USB cable coming off the back of the PC.  Nautilus popped up, showing SAMSUNG...  under Trash.  If I click on SAMSUNG an icon saying "Folder is Empty" appears in the center of the screen.  I turned back to the phone and swiped the encryption thingie to get it active, then clicked on the SAMSUNG icon in Nautilus.  The wheel starts spinning.  If I click on the "Eject" icon a window pops up saying Volume is busy, do I want to Cancel or Unmount Anyway.

I don't know if this helps or not, but another odd thing is that the SAMSUNG... entry remains below Trash in the Nautilus directory even if I unmount the phone or click the power button to put it in hibernation.  The SAMSUNG... tab doesn't go away until I physically unplug the USB cable.  AS soon as I plug the USB cable back in, the SAMSUNG tab pops back up.  

SOMETHING NEW - I just stumbled onto this.  When I plug the phone in (and I think this is something new since adding dev tools or enabling debugging) a little notification comes up on the phone that's easy to miss.  I have to swipe down from the top of the phone.  The notification says "Android System USB for file transfer" with a tiny green arrow indicating options.  If I tap the green arrow, then tap again, I get five options under a header saying "Use USB for"  The five options are "Transferring files", "USB tethering", "MIDI", "Transferring images", and "Charging phone only".  The radio button for transferring files was highlited.  I tapped on "Transferring images".  Nautilus suddenly gave me several folders from the phone.  Alarms, Android, DCIM, Download, Movies, etc.

If I go to DCIM, then "Camera". I get the .jpgs that are on the phone.  Not actual thumbnails, just little dark gray generic .jpg icons.  Ubuntu does the same thing with my Canon T3i.  Just generic icons, not thumbnails.  When clicked on, the generic icons do reveal the image, but this is an annoying regression from previous versions of Ubuntu.  There's a setting in Nautilus that's supposed to allow thumbnails from external sources.  I changed that but it didn't help.  

On the phone, the .jpgs do come up when clicked.  There are some videos on the phone but they do not show up at all.  I tried the other folders but they all show as empty.  I turned back to the phone and changed the radio button to "Transferring files" and Nautilus went back to a spinning wheel and no folders.  If I tapped the radio button on the phone to go back to "Transferring images" again Nautilus got confused, showing the folders but unable to mount them.  

I'm getting the feeling that I might break something if I just keep changing stuff...

---

### Post by yetimon_64 on 2019-11-13
With my Samsung J7 phone I found I only needed to install the mtp-tools package onto Bionic to get full functionallity in the file manager when accessing the phone file system.

Prior to adding that package I could see the phone in the file manager but wasn't able to do much else even with the phone set to "file transfer" on android. It seemed to me that Ubuntu didn't have full file sytem support for android until I added mtp-tools.

I didn't need to enable develloper mode or do anything else with the phone. Just adding full mtp support on Ubuntu 18.04 helped here.

 Strangely enough I am now on Xenial 16.04 without any added mtp support and everything seems to work fine whereas Bionic 18.04 was a bit of a pain to get it working on. With 18.04 I'd suggest you try the mtp-tools package installed onto Ubuntu.

Good luck, cheers, yeti.

---

### Post by Bartender on 2019-11-14
I used the directions on this site 

[https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/mtp-tools_1.1.13-1_amd64.deb.html]("https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/mtp-tools_1.1.13-1_amd64.deb.html")

to install mtp tools via terminal.
  
No difference.  SAMSUNG shows up in the column in Nautilus but if I click on it the wheel just spins.  Try to Eject, Ubuntu says "Volume is busy"

I really hate it when Windows does something better than Ubuntu, but on the Windows PC it "just works".  The File Explorer opens the phone, and I get thumbnails too.  

I just checked to make sure - Nautilus Preferences are set to show "all" thumbnails.  Nautilus acts like no setting was changed.  Won't show thumbnails on external device, but once I import to the hard drive thumbnails work.

---

### Post by ank2 on 2019-11-14
When connected via USB you can use adb on Linux. You probably need to be root (there's a way to setup an udev rule to do this as user).

adb shell allows you to see the Linux running under Android and you can browse directories. If this works, type "exit" to get out. Remember the path where your files are.

Then perform a **adb pull /sdcard/where_ever_the_files_are/* .** That should save the files in the home directory of you Linux machine.

---

