---
title: "rip with no ripper"
date: 2010-11-19
forum: Multimedia Software
---

### Post by shantiq on 2010-11-19
for a bit of fun   the most basic form of copying a disc 

If you want to see a thing of beauty which you can do when you are not online and have not got a ripper installed but have lame and flac installed (of course no tagging since you are not online)


to rip to mp3
============= 


1. insert cd
2. go places/computer
3. right click on cd drive/open
4. drag wav files to a folder on desktop   called  myrip    (right-click create folder)
5. open terminal
6. enter cd ~/Desktop/myrip
7. enter   ```
for f in *.wav; do lame -b 320 -q 0 "$f" "${f%.wav}.mp3"; done
```   



all your files are now mp3   delete wavs manually  or ```
rm *.wav
```



or to do both commands at once ( thank you mc4man)

```
for f in *.wav; do lame -b 320 -q 0 "$f" "${f%.wav}.mp3" && rm "$f"; done
```



to flac
=======


same as before to 6


7. enter  ```
for f in *.wav; do flac --best  "$f" "${f%.wav}.flac"; done  
```



 OR       ```
flac --delete-input-file --best *.wav
```

---

### Post by Jahid65 on 2010-11-19
works great.:p

---

### Post by shantiq on 2010-11-20
wanted to add something to the first one   mp3


to be able to delete the wavs after they have been converted


i tried   ```
if [ i=mp3 ] then rm [ i=wav ] fi 
```   but since i have no idea what i am doing not surprisingly it does not work


Any better offers from guys who actually know how to write a bash-script?  :KS



thanx    shan

---

### Post by mc4man on 2010-11-20
rm *.wav will get rid of the wav's

While clearly using a ripper is best, in context of this thread - 
You don't really need to copy the .wav's first, you can go directly from disk, just cd to the 'location' and run your command with a slight change, - you'll need to output to a dir. somewhere

The typical location is this, the blue may vary, check first
~/.gvfs/'cdda mount on [COLOR="Blue"]sr0[/COLOR]'
To output to a directory just pre-pend "${f%.wav}.mp3" with an existing dir/path
Ex.
~/Music/mp3/"${f%.wav}.mp3"

The other small issue is while your tracks may appear in order in the folder, if you load the folder they will play out of - track 1, then track 10 > 19, then track 2,3 ect. (unless there are 20 or more, then 2, 20 > 29, 3, ect.

So a few options - 
If you had cdda2wav installed (maybe outside of conditions here), then you could use it to record to .wav and proceed as before. However in the cdrecord source there is a small script, cdda2mp3, that will record and output to .mp3 in a 01-.mp3, 02-.mp3, ect. format

To use you'd simply place (preferably) in ~/bin and run with it's name (cdda2mp3

If you have more than one drive it's probable the device won't be found, to fix you can edit CDDA2WAV_OPTS= in the script or just start from the terminal with this, adjusting blue as needed (the export lasts the life of the terminal
export CDDA_DEVICE=/dev/[COLOR="Blue"]sr0[/COLOR]

The normally editable sections of script are here, marked in blue I've added
> # specify the sampling program and its options
# do not specify the track option here!
CDDA2WAV=cdda2wav
CDDA2WAV_OPTS='-H -q'
CDDA2WAV_XOPTS='[COLOR="Blue"]-paranoia[/COLOR] '

# for normal use, comment out the next line
#DEBUG='-d1'

# the post processor is fed through a pipe to avoid space waste
# specify the post processing program and its options
MP_CODER=lame
MP_CODER_HELP=--help
MP_OPTIONS='[COLOR="Blue"]-V 1[/COLOR]'
MP_XOPTS=''

If you take a close look at script you'll see you can use flac instead of lame, also changing a later line, NAME=$TRACK-$FILEPREFIX.mp3 to NAME=$TRACK-$FILEPREFIX.flac

More in line w/ the orig premise, no nothing.
So  one alt. way bypassing copying to wav. Presuming you have a ~/bin (**if not time to make one - mkdir bin and a restart will add to path.**
Ex. want to save as mp3 to Music in a folder to be named anything you want (the question will ask 'name of album', use anything you wish, spaces don't matter, don't use weird characters

Create 2 scripts, **place in the bin in your home folder** and make executable. 
With audio cd in drive navigate to ~/.gvfs and see if different than cdda mount on sr0, if so than adjust first script to match (blue
If you change the name of script 2 from pad1 then also adjust in script 1 (red

Apologizes for script 2- easier for me to do separately and as far as script 2 I'm sure can be done cleaner or both combined in better fashion

script 1, I'll name direct2mp3
```
#!/bin/bash
echo "Name of album?"
A= read A
cd ~/.gvfs/'cdda mount on [COLOR="Blue"]sr0[/COLOR]'
mkdir ~/Music/"$A"
for f in *.wav
do 
lame -V 1  "$f" ~/Music/"$A"/"${f%.wav}.mp3"
done
cd ~/Music/"$A"
rename 's/ /_/g' *.mp3
for f in *.mp3
do
mv $f `[COLOR="Red"]pad1[/COLOR] $f`; done

```

script 2 named pad1
```
#!/bin/bash
num=`expr match "$1" '[^0-9]*\([0-9]\+\).*'`
paddednum=`printf "%02d" $num`
echo ${1/$num/$paddednum}
```

Then just go direct2mp3 from terminal, type in your save folder name and that's that.

---

### Post by shantiq on 2010-11-21
thanx mcman

will take a good look at your "other way"

but to do with my original question and your answer



```
rm *.wav will get rid of the wav's

```


that was my first choice but the problem was i wanted to run the whole thing in just one command

and rm *.wav  if written like this [ [COLOR="Red"]of course do not use :)[/COLOR]]


```
for f in *.wav; do lame -b 320 -q 0 "$f" "${f%.wav}.mp3" ;rm *.wav; done
```    removes all of the wavs after only **one** of the wavs have been converted to mp3

and granted i could run rm*.wav   afterwards but i am after the elegant one command solution how to delay the second command until all the wavs have been converted    

how does one do that? i am sure that is not difficult


Anyway off to explore your alternative it is going to stretch me but good :KS

---

### Post by shantiq on 2010-11-21
ok looked at cdda2mp3    and it is installed by default on ubuntu i think


but i cannot call it ripping without a ripper   tho it is a handy tool



1. just stick cd in and enter ```
cdda2mp3
``` and you will get you disc in your home folder in the default 128kbps which i think is hogwash quality


2. looking around you can hike it to 320 thus

```
cd /usr/bin
```
```
sudo gedit cdda2mp3
```
on line 33 (ithink just have a look) replace with   ```
MP_OPTIONS=${MP_OPTIONS:-'--preset insane'}
```
and save


3.   run ```
cdda2mp3
``` now you have 320kbps


brilliant simple tool

---

### Post by mc4man on 2010-11-21
> ok looked at cdda2mp3 and it is installed by default on ubuntu i think

Just looked, it's not installed by default but is installed as part of a cdda2wav package install.
Myself never looked, had just copied the script from source to ~/bin which trumps the same file if installed in any other bin. (there is also another script installed as part of the cdda2wav install - cdda2ogg

---

### Post by shantiq on 2010-11-21
both really handy


now back to the original quest

any idea how to knock

```
for f in *.wav; do lame -b 320 -q 0 "$f" "${f%.wav}.mp3"; done

```


and 

```
rm *.wav

```


into one line of code which does not remove all the wavs after the first wav has been converted

---

### Post by mc4man on 2010-11-21
```
for f in *.wav; do lame -b 320 -q 0 "$f" "${f%.wav}.mp3" && rm "$f"; done

```
Though as mentioned, in orig. scenario, I'd not bother to copy .wav's to hdd first, nothing to be gained and takes longer

---

### Post by shantiq on 2010-11-22
thank you that really works

---

