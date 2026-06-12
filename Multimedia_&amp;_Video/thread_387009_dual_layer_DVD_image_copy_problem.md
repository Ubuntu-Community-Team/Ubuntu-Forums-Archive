---
title: "dual layer DVD image copy problem"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by deathmonkey on 2007-03-17
Hi all.  I am trying to make a backup copy of a dual layer DVD.  I used the instructions given here:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_burn_Image_.28ISO.29_files_into_CD.2FDVD]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_burn_Image_.28ISO.29_files_into_CD.2FDVD")

Specifically, I did this:
```
sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024
```

to make the image, and then this:
```
Right click on Image (ISO) file -> Write to Disc... -> Write
```

to burn the copy.  Everything appears to work, but the copy won't play.  It shows me the first menu, but then when I click to the next menu (in Totem) I get:

> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I have libdvdcss installed and working.  The orignal disc plays just fine; it's only the copy that gives me the problem.  In a set-top player, I get similar behavior: the first menu shows up, but it just freexes on subsequent menu selections.

Any ideas?

Thanks.

--jim

---

### Post by johnlh on 2007-03-17
DD doesn't always work. Try this link:
[http://www.debiantutorials.org/content/view/10/135/](http://www.debiantutorials.org/content/view/10/135/)
vobcopy method

---

### Post by deathmonkey on 2007-03-17
Thanks for the suggestion.  I read the page, and it seems that the vobcoopy method won't let me back up the whole thing -- just the main feature.

Plus, after I made that post, it ocurred to me to check the iso I had created with dd, and it plays fine in Totem; it's indistinguishable from the original disc.

So the iso appears to be fine, so maybe there was some problem with the burn.  I don't see any configurable options when I right-click and use "write to disc."  Is there another burn method that someone could recommend?  

Thanks.

--jim

---

### Post by deathmonkey on 2007-03-19
So, I just thought I'd provide some closure for this thread:

I worked on this all weekend, and have had to accept limited success.  It seems that there is some sort of copy protection built in, around which there is not yet a way.  I am able to do three things with it:
1) use dd to create a perfect, useable image file on my hard drive;
2) use vobcopy to rip the main feature, which could then be burned onto a backup dvd;
3) use AcidRip to create a compressed .avi of the main feature;

None of these results in a perfect duplicate of the DVD, but I suppose I'll just have to be happy with them.

Thanks again for your help.

--jim

---

### Post by WilliamAnderson on 2007-04-08
Hi deathmonkey,

You are indeed banging into CSS DVD copy protection. A dd copy of the disk makes a bit for bit copy of the data on the disk, but the drive reads a value off of a portion of the physical disk that dd (or any other OS tool) cannot see or write. Without that value, the CSS encrypted content cannot be decrypted.

Of course, if the disk contents were decrypted before being written to the copy, then you would get the whole disk. The dvdbackup utility does this. It can be found in one of the repositories (search on dvdbackup in Synaptic) or installed from source downloaded from their web site [http://dvd-create.sourceforge.net/index.shtml](http://dvd-create.sourceforge.net/index.shtml) . The DVD-Create web site includes documentation that has sample commands to copy a whole dvd or just a single title.

I have used this tool to copy encrypted dvd movies that I own for playing back in the car on trips so that the expensive originals are not damaged. I think that this copying is legal under fair use. 

I hope that this is helpfill.

William

---

### Post by andrew.46 on 2007-08-16
Hi,

 Saw you struggling a little with vobcopy:

> **deathmonkey said:**
> Thanks for the suggestion.  I read the page, and it seems that the vobcoopy method won't let me back up the whole thing -- just the main feature.[...]  Is there another burn method that someone could recommend?  

You may have missed the -m option with vobcopy which will enable you to mirror the *entire* DVD.:
```
    -m, --mirror
              mirrors  the  whole  dvd to harddisk. It will create a directory
              named after the dvd and copy the ifo, bup and vob  files  there.
              The title-vobs are decrypted during this.

```
As for burning just use your favourite burning program: Gnomebaker or whatever although this can also be done via CLI.

                 Andrew

---

### Post by ekravche on 2007-12-08
> **johnlh said:**
> DD doesn't always work. Try this link:
[http://www.debiantutorials.org/content/view/10/135/](http://www.debiantutorials.org/content/view/10/135/)
vobcopy method

I will give 
```
dvdbackup -M -i/dev/cdrom -o/path/to/your/directory (entire disc)
```

a shot

Great it worked. I ran that command, which ripped the entire 8.5 GB dvd to my drive and then I copied the ripped content onto an empty 8.5GB dvd using gnome backer

Thanx for the help.

---

