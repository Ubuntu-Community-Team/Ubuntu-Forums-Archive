---
title: "Can't burn good dvds"
date: 2009-10-02
forum: Multimedia Software
---

### Post by onespeedbiker on 2009-10-02
I have posted several times with my issues with no response. But I'll try again. 

 I have a dvd player and a burner (my dvd burner, Memorex DVD+-RAM 530L, supports most formats; usually I go with DVD+RW and DVD+R). The first major problem occurred when the burner would not operate through /media/cdrom and started creating it's own device name, /media/DVD. When this occurred I could view DVD videos but could not burn, unless I used CD/DVD creator. Any attempted to use line commands or Brasero resulted in a 2-3 second burn and an i/o error message. As I continued to try and force a burn, suddenly the /dev/window popped open on the desktop and everything came back to life. Interestingly enough, I had several clonzilla saves of ubuntu, including a clean install and the cdrom bug as I called it existed as I tried to use different saves. After this behavior my burner started chewing up my DVD+R 2 to1 on most burns and turned half my DVD+RW usless unless I went to Windows and did a full erase on them. The cdrom bug came and went again and now I can only burn DVD+RW and I only get a good burn half the time; even when it seems to be a good burn it will not be readable or play and usually will not mount. The burner works flawlessly in Windows with all media (I saw this, not because I think Windows is better than ubuntu, but to show that my burner is not broken).

The programs I used are; GUI- Brasero, DeVeDe, Winff, CD/DVD creator, k9 copy and K3B. Line commands with ffmpeg, dvdauthor, growisofs. dvd+rw, mkisofs.

---

### Post by mick55 on 2009-10-03
Hi again

I experienced a similar problem with cd burning after
an update.I could not successfully burn a cd in any program,
or from the command line.

For a test i tried burning from the CLI as sudo, and it worked
perfectly.Try burning from th CLI as root and see if it works.

e.g. sudo cdrecord -v speed=4 dev=/dev/xxxx xxxx.iso.

If that works change the permissions on wodim

chmod +s wodim

(cdrecord symlinks to wodim)

Hey, it made me nuts for 3 days, so i can relate

cheers
mick

---

### Post by onespeedbiker on 2009-10-03
> **mick55 said:**
> Hi again

I experienced a similar problem with cd burning after
an update.I could not successfully burn a cd in any program,
or from the command line.

For a test i tried burning from the CLI as sudo, and it worked
perfectly.Try burning from th CLI as root and see if it works.

e.g. sudo cdrecord -v speed=4 dev=/dev/xxxx xxxx.iso.

If that works change the permissions on wodim

chmod +s wodim

(cdrecord symlinks to wodim)

Hey, it made me nuts for 3 days, so i can relate

cheers
mick Okay, slow down a little. I usually use,

 growisofs -Z /dev/scd1 -dvd-video dvd/

would I change that to 

sudo growisofs -Z /dev/scd1 -dvd-video dvd/  ?

Thanks, brad

---

