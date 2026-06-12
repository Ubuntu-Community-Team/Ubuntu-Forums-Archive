---
title: "Mythburn - Mytharchive DVD not readable, but plays in some dvd players"
date: 2008-06-25
forum: Mythbuntu
---

### Post by neoneddy on 2008-06-25
Been rocking MythBuntu for a while now, but I've been archiving NASCAR races for my father-in-law, not my favorite but ya know.

I tested the dvds in the MythBuntu Box, and 2 hardware DVD players, it works in all 3 devices, however they do not play in my father-in-law's dvd player, nor in any computer I've tried.

I just did an update from 8.04 beta to 8.04 final, so the system is up to date.

I've attached 2 screen captures of the data I see.

Help. Please! :-)

---

### Post by agamotto on 2008-06-26
There do seem to be quite a few problems with DVDs created with MythTV and certain DVD players.  Essentially, it boils down to not using animated menus, also, don't expect them to work on many DVD players made before 2004.

---

### Post by neoneddy on 2008-06-26
actually I used no menus and the problem really is no computer I try can read the data, no video_ts folder, nothing. Please help :-)

---

### Post by dsegel on 2008-06-29
MythArchive's been around for a while now but has never worked as well for me as the simple combination of dvdbackup and mkisofs. I hadn't used MythArchive for about a year but tried just today because I figured they must have made advances. No such luck. Making the iso was easy enough, but the video had heavy pixelation at parts (which makes no sense since there's supposed to be no processing when making an iso) and the menu was slower than the copy I made with dvdbackup and mkisofs.

For reference, here's how I do it (in a terminal window):

1. Move to a directory that you want to store the files in
2. do a 'dvdbackup -i /dev/dvd -M -o .'
2. do a 'mkisofs -dvd-video -o DVD_TITLE.iso DVD_DIR/

This could be easily scripted. DVD_DIR is whatever dvdbackup named the directory it dumped the files in - it gets the name from the DVD usually. Note that this creates an iso file that is an exact duplicate of the original - not transcoded to fit on a single-layer DVD. The iso file you end up with is called DVD_TITLE.iso (obviously you'd want to use a real name, like Transformers.iso in the mkisofs command) which you can then watch via MythVideo (with the internal player or xine), XBMC, or burn to a dual-layer disc. I've only ever burned a DVD once, and I used Windows to do it so don't ask me for help with that. This process works on about 95% of the DVDs out there; some use newer copy protection methods that dvdbackup can't handle. The results with the proper play are indistinguishable from the original DVD.

---

### Post by neoneddy on 2008-07-08
I'm not interested in copying a dvd, just these stupid NASCAR races for my father-in-law :-)

I tried using projectX as a possible variabl, but that failed on execution.

I'm now taking the dvd's one by one loading them into the mythtv box and ussing SSHFS on my mac to pul the VIDEO_TS folder off and then I plan to reburn.

I think I may be onto something though, maybe it is jsut the act of burning that is causing issues, like the exact dvd writing commands or something, I'm also trying different brand DVD's now as well.

Wierdest thing though, these dvd's play in all of hardware dvd players and the mythtv box, but no computers, mac, pc or otherwise.

This is also configured as a set-top box in case anyone cares.  Thanks for all the help, I'll post back how the reburn goes, any other suggestions?

---

### Post by neoneddy on 2008-07-13
ok, I now tried something else, I made an iso image, rather than a burned dvd.

the iso mounts but still shows no files.

I'm putting the blame squarely on growisofs or mkisofs

attached a screenshot of the mounted iso.

---

### Post by neoneddy on 2008-07-13
```
 if drivestatus == CDROM.CDS_DISC_OK or drivestatus == CDROM.CDS_NO_INFO:
            if mediatype == DVD_RW and erasedvdrw == True:
                command = path_growisofs[0] + " -dvd-compat "
                if drivespeed != 0:
                    command += "-speed=%d " % drivespeed
                command += " -use-the-force-luke -Z " + dvddrivepath
                command += " -dvd-video -V " + title + " "
                command += os.path.join(getTempPath(),'dvd')
            else:
                command = path_growisofs[0] + " -dvd-compat "
                if drivespeed != 0:
                    command += "-speed=%d " % drivespeed
                command += " -Z " + dvddrivepath + " -dvd-video -V " + quoteFilename(title) $
                command += os.path.join(getTempPath(),'dvd')

```

Here is an excerpt from mythburn.py in /usr/shar/mythtv/mytharchive/scripts/mythburn.py 

I have a somewhat working knowledge of programming, but I know nothing of python.  I was just checking for -dvd-compat and it seems to have it.

---

### Post by ninti on 2008-07-24
I have almost the exact same problem. I made a DVD through mytharchive, and the DVD plays fine in Myth. But my DVD player refuses to play it. My Windows computer says the disc is blank, no sub-dirs like video_ts...nothing. Very wierd. 

Edit: I created another one with no menus, and same thing.

---

### Post by neoneddy on 2008-07-24
all this time I was beginning to think I was crazy.

My only solution so far has been to burn the DVD, then browse the mythtv filesystem with sshfs , download the video_ts folder, then reburn. 

But again I'm 100% sure this is an issue with the ISO creation, not the burning hardware.  At this time I'm also fully updated and patched.

---

### Post by Nikas on 2008-08-02
I'm having the same problem. :(

Using Weekly builds.

The DVD's just don't work. :(

---

### Post by neoneddy on 2008-08-02
We've got to do something to get this some more exposure.  I'll spray paint it on an overpass.

---

### Post by Nikas on 2008-08-02
Can someone file a bug report? Hmm.. or look for a existing report..

Edit:
I can't find any report about this problem.
Help me look.
[http://svn.mythtv.org/trac/](http://svn.mythtv.org/trac/)

My computer or my Mythbox can't read the DVD's.

---

### Post by Nikas on 2008-08-16
Got some new -fixes-builds the other day.
Same problem. :-(

---

### Post by Timuntu on 2008-08-23
This might be from a genisoimage bug.

[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942")

[http://ubuntuforums.org/showthread.php?t=787299&highlight=genisoimage]("http://ubuntuforums.org/showthread.php?t=787299&highlight=genisoimage")

Taking out the "--dvd-video" options in the mytharchive script or down grading to a previous version of genisoimage seems to work for me to get the DVD readable in windows XP.

---

### Post by neoneddy on 2008-08-23
forgive me, can you  do an apt-get downgrade *app-name* ?

---

### Post by Nikas on 2008-08-23
Edited: See my post #18.

---

### Post by neoneddy on 2008-08-23
I'll try it here on Monday, I have to burn some nascar races for the father-in-law.

---

### Post by Nikas on 2008-08-23
This is how i got it to work:

wget [http://ftp.se.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.8-1+b1_i386.deb](http://ftp.se.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.8-1+b1_i386.deb)
sudo dpkg -i genisoimage_1.1.8-1+b1_i386.deb

Have fun!

---

### Post by neoneddy on 2008-08-25
Awesome!

This makes this mythbox about twice as useful!

---

### Post by neoneddy on 2008-08-26
```
shawn@MythTV:~$ sudo apt-get install -i genisoimage_1.1.8-1+b1_i386.deb
[sudo] password for shawn: 
E: Command line option 'i' [from -i] is not known.
```

This is what I get when trying to use the -i switch


** FIX ***

I used 
sudo dpkg -i genisoimage_1.1.8-1+b1_i386.deb

Seemed to work fine

---

### Post by MykeBuntu on 2008-12-22
I am having some similar issues attempting to create a DVD via Mytharchive... I'm VERY new in Mythtv... 

If I run *just* the 2 commands from post #20 (looks like step 1 loads the named package and step 2 resets/inits it) then I should be able to burn a DVD that will play in a Buntu box, a Windows box, and some home theater DVD players? The one I've managed to create so far does play in my home theater DVD but I see nothing when put into a Windows box-- looks like a blank disk named MythTv.

A question about loading a package as in post 20 step 1: what are the gotchas you (may?) encounter by bypassing the Synaptic Package Manager? I've seen other places where people have advised a manual install-- and often someone pops up soon after and warns of various dire consequences of not using SPM... are these cases where the system won't know if you already have some component installed-- and may then (next time you use SPM) try to overwrite something you already installed and cause issues?

---

