---
title: "Script: Rename &amp; Move TV Show Downloads"
date: 2011-02-05
forum: Multimedia Software
---

### Post by bemental on 2011-02-05
Hello!

Just built myself an HTPC from scratch and installed Ubuntu 10.10 on it (using XBMC for now).  I'm familiar with Linux and have been dabbling with it for many years but in the end my main computer runs OS X.

Trying to modify a script I found elsewhere that will auatomagically rename and move downloaded TV shows into a preexisting file hierarchal system.  I have an automator function on my Mac that was put together for PLEX but it will obviously not run in Ubuntu.

Here's what I've got so far.  Remind you I'm not much of a programmer:


```
!/bin/bash
cd /home/htpc/Downloads
ls -1 *.mkv |
while read filename
do
newPath=`echo $filename|sed "s/\(.*\)S0\{0,1\}\([[:digit:]]\{1,2\}\)E[[:digit:]]\{2\}.*/\1\/Season \2/" | tr "." " " | sed "s/ \//\//"`
mv -v $filename "/home/htpc/Media/TVShows/$newPath/$filename"
done
```

Here's the example (failed) output that I'm currently receiving:

```
htpc@HTPC ~ $ Desktop/TVRenamer\ Linux 
Desktop/TVRenamer Linux: line 1: !/bin/bash: No such file or directory
mv: target `/home/htpc/Media/TVShows/Bones -/Season 6/Bones - S06E01.mkv' is not a directory
```

So basically, the script is finding the file to be moved fine, is almost correctly identifying the new file structure location (minus those dashes it's trying to throw in) but it still gets stuck.

Any ideas?  Thanks in advance!

---

### Post by Zzzk on 2011-02-05
Shouldn't the first line be - #!/bin/bash ?

---

### Post by DaithiF on 2011-02-06
when mv complains that the target isn't a directory, it means that you are trying to move more than 1 source file to a target that is a file rather than a directory.

to illustrate, if you do:
mv file1 file2 file3
you get an error because you you're trying to move 2 source files into 1 target file ... that doesn't make sense.

whereas if you say:
mv file1 file2 dir1
then thats fine, because when the target is a directory you can move as many files as you want into it.

you may be wondering what this has to do with your problem .... well it looks like your source file has spaces in its name, which to the mv command looks like several files rather than one.  The solution is to enclose it in quotes (as you did with the target parameter):
```
mv -v "$filename" "target..."

```

---

### Post by bemental on 2011-02-06
> **DaithiF said:**
> when mv complains that the target isn't a directory, it means that you are trying to move more than 1 source file to a target that is a file rather than a directory.

to illustrate, if you do:
mv file1 file2 file3
you get an error because you you're trying to move 2 source files into 1 target file ... that doesn't make sense.

whereas if you say:
mv file1 file2 dir1
then thats fine, because when the target is a directory you can move as many files as you want into it.

you may be wondering what this has to do with your problem .... well it looks like your source file has spaces in its name, which to the mv command looks like several files rather than one.  The solution is to enclose it in quotes (as you did with the target parameter):
```
mv -v "$filename" "target..."

```

Thanks Daith, I'll have to let you know how it goes - the weekend is over so it's back to the daily grind.

Again, thanks for the help!

---

### Post by bemental on 2011-02-06
> **Zzzk said:**
> Shouldn't the first line be - #!/bin/bash ?

Probably - would avoid spitting out that crazy bin/bash error!

---

### Post by bemental on 2011-02-06
Yea... didn't work out with the suggested changes.



```
htpc@HTPC ~/Downloads $ ~/Desktop/TVRenamer\ Linux 
`Bones_S06E01.mkv' -> `/home/htpc/Media/TVShows/Bones_/Season 6/Bones_S06E01.mkv'
mv: cannot move `Bones_S06E01.mkv' to `/home/htpc/Media/TVShows/Bones_/Season 6/Bones_S06E01.mkv': No such file or directory
```


I've got a workaround right now using the previously mentioned automator actions on my iMac to change the file names and put them in the appropriate file hierarchy.  

Actually works well because then I can still use the iMac as my main downloading machine keeping the HTPC and flat screen LCD TV off when not in use.  I can only imagine they're two of the biggest vampires in the house (and since the iMac is on most of the days anyway it isn't too big of a deal).


Keep the replies coming though if anyone has any other suggestions!

---

### Post by DaithiF on 2011-02-07
do the target directories already exist?  ie. Bones_/Season 6/ etc?  Nothing it the script excerpt you posted will actually create directories, so unless you have separately created those thats likely the problem.

---

### Post by aeiah on 2011-02-07
> **DaithiF said:**
> do the target directories already exist?  ie. Bones_/Season 6/ etc?  Nothing it the script excerpt you posted will actually create directories, so unless you have separately created those thats likely the problem.

yea this seems like a likely culprit. you should easily be able to create the required directories with mkdir -p. unlike the standard mkdir, mkdir -p will create all necessary directories along the way

since you've already got a $newPath variable, you could just add this line before doing the moving:
```

mkdir -p "/home/htpc/Media/TVShows/$newPath/"

```

---

### Post by bemental on 2011-02-07
> **DaithiF said:**
> do the target directories already exist?  ie. Bones_/Season 6/ etc?  Nothing it the script excerpt you posted will actually create directories, so unless you have separately created those thats likely the problem.

I had a feeling that might be the problem, although it seems that there is a formatting error in the transitioning from the downloaded file naming scheme to the new, "streamlined" name.

All those spaces, dashes, dots (etc) that are usually included in names are causing it to spit out "unclean" file names which in turn is destroying the name of the soon-to-be created directory (i.e. "Bones_/"

---

### Post by bemental on 2011-02-07
> **aeiah said:**
> yea this seems like a likely culprit. you should easily be able to create the required directories with mkdir -p. unlike the standard mkdir, mkdir -p will create all necessary directories along the way

since you've already got a $newPath variable, you could just add this line before doing the moving:
```

mkdir -p "/home/htpc/Media/TVShows/$newPath/"

```

Aeiah, I'll give it a shot when I get home.  Unfortunately I turn the HTPC off for the day so I'm unable to SSH into it from work to give it a test (probably for the better since otherwise I wouldn't get anything done!).

Thanks for the help, I'll let everyone know how it turns out.

---

