---
title: "How to defrag a FAT32 USB-stick in Ubuntu?"
date: 2010-04-24
forum: Multimedia Software
---

### Post by private_lock on 2010-04-24
How to defrag a FAT32 USB-stick in Ubuntu?

When my parents got a new 16:9-television I found, it has a USB-slot to display photos. So I bought a new 2 GB USB-stick for them and copied over some photos. Well it works quite well, if you organize the photos in folders (because a flat list is simply unmaintainable).

I really spent some time to work this out on my laptop. But the next day I showed it to my parents on their TV, the photos came in seemingly random order. Taking a second look the order is not really random, but shuffled once for all time. The television does no sorting at all and shows the photos in the order, the files were added to the directories.

As I understand from the documentation of the TV, defragmentation can not only rewrite files so their contents are in a neat sequence, but also reorganize folders and especially sort the entries. There is just one problem: My last WinXP-PC was already recycled, though I still have the installation-CD.

Now I definitely don't want to install WinXP everytime over Ubuntu, just to do some defragmentation now and then. Moreover I don't want a dual-boot, as it would tempt me, to abandon Ubuntu and switch back to WinXP.

On the other hand, I don't want to bother my friends with this little problem, as far as admitting, there are things I simply cannot do with Ubuntu won't help me persuade them, that Ubuntu is a veritable replacement.

Finally the TV and the stick are at my parents home which is quite a distance away. I imagine bringing more photos on my laptop *TO* them, but not taking the stick with me every-time, just to "repair" it on some WinXP-PC somewhere far away, thereby effectively taking all the other photos away *FROM* them.

Getting more specific:

1. Are there any defragmentation / reorganization / reparation tools to maintain FAT32 under Ubuntu?

2. Has anybody ripped Scandisk+Defrag from WinXP and got it running with wine? Is this save in the way, that it will not damage the FAT32 filesystem?

3. I've installed WinXP in VirtualBox from Sun (not the OSE-version). But so far I could not access any USB device. The menu-entry in virtualbox is simply grayed out.

4. More ideas?

Kind regards
private_lock

PS: To cut some unnecessary post:
- I'm well aware, that Linux has a proper filesystem, that does not need defragmentation on a daily basis.
- FAT32 is a pain in the ***, no need to tell me: But that's all the TV understands! So no reformating advice please.

---

### Post by Chronon on 2010-04-25
You can tar and untar the partition.
[http://www.keyongtech.com/4564818-how-to-defrag-a-fat32](http://www.keyongtech.com/4564818-how-to-defrag-a-fat32)
```

tar czvfC /tmp/dos.tgz /mnt/dos .
rm -fr /mnt/dos/*
tar xzvfC /tmp/dos.tgz /mnt/dos
```

---

### Post by Espionage724 on 2010-04-25
I heard you didn't need to/not supposed to defrag a solid-state drive (flash drives and SSD's)

---

### Post by private_lock on 2010-04-25
@Chronon

That looks really promising, though it is very close to reformating the drive *sigh* ... I'll definitely test it ... it just takes some time, until I visit my parents next time.

@Espionage724

You're absolutely right. Every write to SSD degrades the hardware a little. So every memory cell only supports a limited number of writes. Once one cell fails, a whole block gets marked as unusable. To be honest: that's a strong indication, to exchange the whole drive. But as the stick was only three weeks ago, I'm not really concerned about it's lifetime right now.

This situation is somewhat unique, as of the fact, that each file was copied in one piece. The only editing that occurred was renaming and moving to other folder locations. So without checking I guess that the files are not fragmented at all and a standard defragmentation should rewrite the directory-entries and finish quite fast.

@ll

OK, now I seem to have a workaround for my imminent problem, though, it's far from being elegant: rewriting the whole drive just to add some more photos. I'm still open for more ideas. And I want to see, if I can get the combo of VirtualBox and WinXP to access the drive. This would also allay my other fear:

What happens when a FAT32 gets into trouble?
How to resurrect data?
How to repair it?

I see the point of Linux saying that the outdated FAT32 is not their responsibility. But we're living in a M$-world and there are more people with blinkers down the line of those constructing a television, that only accesses FAT32 and nothing else.

Hoping for more input
private_lock

---

### Post by Chronon on 2010-04-25
You can repair the file system with fsck.vfat.  I use FAT32 on all of my media players and flash drives because I would like to be able to write to them from any system that I might want to attach them to.

I agree with Espionage724 that it probably isn't worthwhile for the case of a flash device. There's a flash translation layer, meaning that logical addresses don't have any direct relation to physical layout.

Also, flash can access any location equally quickly.  You don't have to wait for a platter to spin up and a read/write head to fly out to the correct position to read some data.  You just set the address you want to read from and a logic level gets read into a register.  I would guess that there is not a measurable difference between access time for a fragmented file and one that isn't.  Flash translation layer means that defragmenters can only arrange files so that they use contiguous logical addresses.  There's no way to guarantee physical defragmentation as far as I know.

---

### Post by RedRat on 2010-04-25
This is really not answering your question, but how about just burning the images to a CD or DVD disk? Most modern DVD players, more than likely those with usb ports, can usually read jpg files and even produce a slide show.

---

### Post by jj-guitar on 2010-04-26
> **Chronon said:**
> You can repair the file system with fsck.vfat.  I use FAT32 on all of my media players and flash drives because I would like to be able to write to them from any system that I might want to attach them to.

Hi Chronon,
 trying to use the fsck.vfat on my usb drive (no stick but a USB-HDD) it posts an error, only FAT 1 and 2 are valid, not 0. Since this tool says to be from 2005, is there an alternative tool to be used with current FAT systems? 

 regards jj-guitar

---

### Post by Chronon on 2010-04-26
What file system is on the HDD?  I have used this tool to fix file system errors on FAT32 drives on a number of occasions.

Can you post the exact output of the error message you're getting?

---

### Post by private_lock on 2010-08-02
Hello!

So, finally I found a workaround, to sort the entries within a directory. I just need to move them to another directory. As a side-effect mv will sort the entries before writing them to the new directory. I havn't checked what happens, if you merge a directory into existing content of another directory. By the way ls -lU will give the unsorted order (the same that the TV-set uses) just to check quickly, that it's working.

The whole thing is wrapped up in a bash-shell-script:

Usage: bash folderSort.sh <directories>

It will recursively work through the directory and all subdirectories and sort them for filename.
BEWARE: Don't apply to the root directory of a media, as the temporary copy is not guaranteed to be on that very same media, which might result in shuffling all your data over to your harddrive, leaving you with an empty usb-stick.
The modification dates of all directories are lost (the timestamps of files are unchanged). To remedy this a little, I just set the dates of the latest modified file within each directory respectively.

Hope this might be useful for anyone.
private_lock

Here is the script I use:
```

#!/bin/bash

# Recursively descend in a folder-structure and recreate every folder on ascending, to ensure it is
# sorted (check with 'ls -lU'). This will defrag the FAT32 file-system but not touch the files.



# count some statistics
directories=0
invalid=0
unreadable=0



# the latest modification date of a file within the given directory
function getMaxDate {
    # read the output of ls (one file per line, sorted for descending modification time)
    ls -1t "$1" | while read line; do
        # "return value" is piped through standard out
        echo "-d $(stat -c %y "$1"/"$line")"
        # stop after first line
        return
    done
}



# expect a single directory as argument
function rewrite {
    # get canonical path
    local canonical="$(readlink -f "$1")"
    if [[ ! -d "$1" || -h "$1" ]]; then
        echo "Skipping symbolic link \"$1\" -> \"$canonical\"!"
        let invalid+=1
        return
    fi
    if [[ ! -d "$1" || -h "$1" ]]; then
        echo \"$canonical\" is not a valid directory!
        let invalid+=1
        return
    fi

    cd "$canonical"
    if [[ $? != 0 ]]; then
        echo Cannot change to directory \"$canonical\"! Skipping ...
        let unreadable+=1
        return
    fi
    echo $canonical
    let directories+=1

    local isEmpty=true
    # recursive descend
    for d in *; do
        if [[ -d "$d" ]]; then
            rewrite "$d"
        fi
        let isEmpty=false
    done

    # ascend to parent of canonical (But don't ascend blindly)
    cd "$canonical"/..

    if [[ $isEmpty == true ]]; then
        # no need to recreate an empty directory, as it's zero entries are always sorted
        return
    fi

    # check for an empty temporary directory-name
    local tempdir="$canonical".bak
    if [[ -e "$tempdir" ]]; then
        # echo $tempdir exits
        local counter=1
        while [[ -e "$tempdir$counter" ]]; do
            # echo ${tempdir}${counter} exits
            let counter+=1
        done
        tempdir="${tempdir}${counter}"
    fi

    # TODO check file-system boundaries (don't move across)

    # rename the current directory
    mv "$canonical" "$tempdir"
    # create a new directory
    mkdir "$canonical"

    # move all the content from the old to the new directory
    # The whole script is build around the side-effect of mv to sort the entries.
    mv "$tempdir"/* "$canonical"

    # check, that the old directory is really empty
    if [[ "$(ls -A "$tempdir")" ]]; then
        echo ERROR: "$tempdir" is not empty!
        exit -2
    fi
    # restore permissions
    chmod --reference="$tempdir" "$canonical"
    # delete the old directory
    rmdir "$tempdir"

    # update the timestamp of the new directory
    # start off with today
    local maxDate=$(date)
    # evaluate the latest modification time of a file within this directory
    # empty directories would be set to now
    touch "$(getMaxDate "$canonical")" "$canonical"
}



# check commandline for help option
for a in "$@"; do
    if [[ ${a} = "-?" || ${a} = "-h"  || ${a} = "--help" ]]; then
        echo -e "\nUsage: folderSort [-?|-h|--help] [directories]\n"
        exit -1
    fi
done

# start processing the directories
if [[ "$#" -eq 0 ]]; then
    # no commandline argument was given -> work on the current directory
    rewrite .
else
    for a in "$@"; do
        rewrite ${a}
    done
fi

echo Processed a total of $directories directories!
if [[ $invalid > 0 ]]; then
    echo Found $invalid invalid directories!
fi
if [[ $unreadable > 0 ]]; then
    echo Found $unreadable directories, that could not be changed into!
fi

exit $(($invalid + $unreadable))

```

---

