---
title: "Unable to view audio/video properties since clean Karmic install"
date: 2009-11-13
forum: Multimedia Software
---

### Post by shanksy75 on 2009-11-13
I recently performed a clean install as I wanted to move over the ext4 filesystem.  I am running Karmic 64 bit.

I cannot for the life of me get the audio/video properties tab to work anymore.  
As I understand it this info is drawn from the totem-common package which I have installed and re-installed.
I have also tried installing many of the gstreamer additional codec packs.

I rely heavily on this to identify both the audio and video codecs and the resolution.

Can anyone help..... Is there any other program I can use in the mean time?

Thanks in advance.

---

### Post by mc4man on 2009-11-13
> is there any other program I can use in the mean time?

mediainfo is superior as  far as total info and accuracy

get here, requires 3 packages min, installed from bottom to top

(libzen0, libmediainfo0, gui

The jaunty packages are fine in karmic

You'll find in Applications -> Sound & Video

Best to open files in the 'easy' view, then for add. info move to html or text if you need to copy out.

Can also be used by dropping file on (in easy view) or set up a r.click option 'open with'
(you'll need to go to open with -> other application to get into the 'open with' menu

[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

Edit 
Don't use the ppa's, better directly from link

---

### Post by shanksy75 on 2009-11-13
Thanks for the quick response mc4man,

However, on install of the first package libzen0 the installer tells me :
Error: Dependency is not satisfiable: libzen0 (>= 0.4.9)

Have I got the right file?  I downloaded the libzen0-dev_0.4.9-1_amd64.Ubuntu_9.04.deb
?

---

### Post by mc4man on 2009-11-13
No, 
give me a second to ck., the files for libzen0 appear to be missing (you don't want or need the -dev's


Edit>
**sorry** about this but it seems libzen0 failed to build correctly for amd_64, will look into

---

### Post by mc4man on 2009-11-13
the ppa for mediainfo has libzen0, but failed to build the other packages
  sourceforge failed libzen0, but has the other 2


Edit 
unfortunately both sourceforge and the ppa have made a mess of mediainfo, too bad.
If I can square away I'll repost, very sorry

---

### Post by shanksy75 on 2009-11-13
ok appreciate the efforts mate

---

### Post by mc4man on 2009-11-13
It appears mediainfo has upped to a new version(..25) but failed to build libzen0 or hasn't built it yet. (may show up shortly

The ppa is a bit of a mess, but the last successfull builds are available in the archive (..20)

I'm on i386, went ahead and did good builds of the latest, though would need to boot to a amd live cd to produce and ck. 64 bit versions

The only one missing is the libzen0, could attach here later

so you could wait for that and in meantime grab the libmediainfo and gui packages from sourceforge ( not the devel

Otherwise here are the links for last good builds on ppa, scroll down to find .debs (you could try these and then update later, to update just follow the order one at a time

[https://launchpad.net/~shiki/+archive/mediainfo/+build/1126007](https://launchpad.net/~shiki/+archive/mediainfo/+build/1126007)

[https://launchpad.net/~shiki/+archive/mediainfo/+build/1151833](https://launchpad.net/~shiki/+archive/mediainfo/+build/1151833)

[https://launchpad.net/~shiki/+archive/mediainfo/+build/1152757](https://launchpad.net/~shiki/+archive/mediainfo/+build/1152757)

---

### Post by mc4man on 2009-11-14
Till mediainfo (sourceforge) gets a libzen0 up here's the latest for amd64

Install this first then libmediainfo0 and the gui (mediainfo-gui) from the mediainfo page linked

works fine on a 9.10 64 bit install, see screen from livecd


edit:

Because I see other using this libzen0, to make sure it's matched with current libmediainfo and mediainfo (gui and or cli) this is where you get those 2 packages

32 bit libzen0 avail. upon request

[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

---

### Post by shanksy75 on 2009-11-14
OK I now have installed and works a treat!

Appreciate the help mate, cheers

---

### Post by matemaciek on 2009-11-14
Thanks a lot guys, I've encountered same problem few days ago and 've been waiting for karmic to appear in [http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/](http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/) ... Tried installing from deb's, but couldn't found libzen0 (; Thanks to you all seems to work! (:

---

### Post by shanksy75 on 2009-11-15
As an update I just thought I would add that now my torrents have finished I have performed a reboot and the audio/video properties tab is now working fine.  I'm slightly embarrassed I didn't think of the obvious before posting I should know better by now.

On the other hand mediainfo is far better so I will keep using anyway!

---

