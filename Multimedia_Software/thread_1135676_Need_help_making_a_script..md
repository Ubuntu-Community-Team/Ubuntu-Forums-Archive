---
title: "Need help making a script."
date: 2009-04-24
forum: Multimedia Software
---

### Post by detroit/zero on 2009-04-24
I have a folder full of episodes of TV shows. I like to play several of them while I'm falling asleep.

I've fallen into a rut lately, and seem to be playing the same ones over and over. What I'd like to do is:

1. Generate a list of all the episodes of all the shows that live in this directory (in various folders/subfolders/etc). That's easy enough with *ls -R /path/to/file*.
2. Pick six random items off the list.
3. Have VLC play those six items and stop.

Ideally, this would be a taskbar launcher or some such thing, but even if I could make it a command I could issue from a terminal or alt+f2, that's just as good.

I know how to generate the list, and I know how to launch VLC from a command line with various options, but I don't know how to pick random items off my list, and I don't know how to make VLC play six items then stop.

Any help/pointers/advice would be appreciated.

---

### Post by detroit/zero on 2009-04-25
Here's what I have so far.

The randomness is non-existant; it just keeps playing the last file in the list. Also, once the randomness is achieved, I have no clue how to make it repeat the selection and play the video six times and then stop.

Thanks for any help.

```
#!/bin/sh
#
# Creates a list of all files in all Simpsons foldersm and then plays six random episodes
# with VLC Media Player.

# Filenames and paths
path1=/home/zero/Videos
path2=/home/zero/Desktop
list=/home/zero/Videos/vids

# Check for the list. If it exists on the Desktop, move it to Videos. If it's in Videos, fine.
# If it doesn't exist, create it in Videos.
if [ -f $path2/vids ]
 then
  echo "VIDS list found on desktop! Moving to $path1" && mv $path2/vids $path1
   else
    echo "VIDS list not found on Desktop - changing to Videos folder." && cd $path1
    fi
if [ -f $path1/vids ]
 then
  echo "VIDS list found in Videos folder!"
   else
    echo "VIDS list not found on Desktop or in Videos... Creating list in Videos folder." && ls -R ~/Videos > $path1/vids
    fi
echo "Done. Filename is:" 
echo $list

# Read the list, select one random line.
LowerBound=1
RandomMax=32767
UpperBound=$(cat $list | wc -l)
RandomLine=$(( $LowerBound + ($UpperBound * $RandomMax) / ($RandomMax + 1) ))

# Use sed to grab the random line.
episode=$(sed -n "$RandomLine{p;q;}" "$list")

# open the random line in VLC
vlc -vvv --fullscreen "$episode"
exit
```

---

### Post by detroit/zero on 2009-04-26
Here's the final version. Fully operational, the script makes a list of all the Simpsons episodes I have, picks a random item off the list and plays it with VLC. It does this six times before exiting.

The number of anything to be played, the paths to the files, etc.. all can be easily changed for anybody else who wants to use it.

```
#!/bin/bash
#
# Creates a list of all files in all Simpsons folders and then
# plays six random episodes with VLC Media Player.
# Created by Uncertain

# Filenames and paths.
path1=/home/zero/Videos
path2=/home/zero/Videos/Simpsons
list=/home/zero/Videos/episodes.txt
# Set the number of episodes to play.
repeat=6
cycles=0
while  [ $cycles -ne $repeat ]
 do
  echo $cycles
  cycles=$(( $cycles + 1 ))
# Check for the list. If it's in ~/Videos, fine.
# If it doesn't exist, create it in ~/Videos.
if [ -f $path1/vids ]
 then
  echo "Episodes list found in Videos folder!"
   else
    echo "Episodes list not found in Videos folder. Creating list..." && cd $path1 && find Simpsons > $list
fi
# Echo the filename of the list, just because.
echo "Done. Filename is:" 
echo $list
# Read the list, select one random line.
LowerBound=1
RandomMax=32767
UpperBound=$(cat $list | wc -l)
RandomLine=$(( $LowerBound + ($UpperBound * $RANDOM) / ($RandomMax + 1) ))
# Use sed to grab the random line.
episode=$(sed -n "$RandomLine{p;q;}" "$list")
# open the random line in VLC
vlc -vvv --fullscreen "$episode" vlc:quit
# Close the cycle count loop...
  done
# ...and exit the program.
exit

```

---

