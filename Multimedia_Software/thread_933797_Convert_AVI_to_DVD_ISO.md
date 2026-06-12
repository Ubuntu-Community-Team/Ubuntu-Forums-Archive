---
title: "Convert AVI to DVD ISO"
date: 2008-09-29
forum: Multimedia Software
---

### Post by rfrayer on 2008-09-29
if your like me youd like to have your cake and eat it to .. meaning 1 comand then burn. this may allready be in my repositorys as a deb (link in my signature). so here goes

```
sudo aptitude install ffmpeg mencoder lame dvdauthor lame-extras libtwolame0 genisoimage
```

sudo gedit /usr/bin/avi2dvd

paist this into the file and save

```
#!/bin/bash

output=$1
####################
# avi     Function #
####################

function avi {
    mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=xvcd -vf scale=352:196,expand=352:240,harddup -srate 44100 -af lavcresample=44100 -lavcopts     vcodec=mpeg1video:keyint=18:vrc_buf_size=327:vrc_minrate=1152:vbitrate=1152:vrc_maxrate=1152:acodec=mp2:abitrate=224 -ofps 30000/1001 -o output.mpg "$output"
}

####################
# rmavi Function #
####################

function rmavi {
    rm *.avi
}

####################
# vcd     Function #
####################

function vcd {
    ffmpeg -i output.mpg -target ntsc-dvd -aspect 4:3 output2.mpg
}

####################
# rm1mpg Function #
####################

function rm1mpg {
    rm output.mpg
}

####################
# convert Function #
####################

function convert {
    dvdauthor -o dvd -t output2.mpg
}

####################
# rmpg     Function #
####################

function rmpg {
    rm output2.mpg
}

###################
# Rename Function #
###################

function finalize {

dvdauthor -o dvd -T

}

#####################
# ISO Function      #
#####################

function image {

mkisofs -dvd-video -o dvd.iso dvd/

}

#####################
# rm2 Function      #
#####################

function rm2 {

rm -rf dvd/

}


###############
# Script      #
###############

avi ;
rmavi ;
vcd ;
rm1mpg ;
convert ;
rmpg ;
finalize ;
image ;
rm2 ;


exit
```

sudo chmod 755 /usr/bin/avi2dvd

play your avi file into a directory of your choice and cd into it

cd /home/someuser/avidirectory

run this comand

avi2dvd *

it takes about an hour but the end result is an iso to burn using your favorate cd burning software k3b, nero etc

---

### Post by mlnease on 2009-05-04
rfrayer, you're a living god.  Thank you.

---

### Post by pastalavista on 2009-05-04
I just installed devede. Haven't used it yet (need to buy some blank disks) but it's supposed to do what your script does in a GUI.

---

### Post by mlnease on 2009-06-09
> **rfrayer said:**
> if your like me youd like to have your cake and eat it to .. meaning 1 comand then burn. this may allready be in my repositorys as a deb (link in my signature). so here goes

```
sudo aptitude install ffmpeg mencoder lame dvdauthor lame-extras libtwolame0 genisoimage
```

sudo gedit /usr/bin/avi2dvd

paist this into the file and save

```
#!/bin/bash

output=$1
####################
# avi     Function #
####################

function avi {
    mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=xvcd -vf scale=352:196,expand=352:240,harddup -srate 44100 -af lavcresample=44100 -lavcopts     vcodec=mpeg1video:keyint=18:vrc_buf_size=327:vrc_minrate=1152:vbitrate=1152:vrc_maxrate=1152:acodec=mp2:abitrate=224 -ofps 30000/1001 -o output.mpg "$output"
}

####################
# rmavi Function #
####################

function rmavi {
    rm *.avi
}

####################
# vcd     Function #
####################

function vcd {
    ffmpeg -i output.mpg -target ntsc-dvd -aspect 4:3 output2.mpg
}

####################
# rm1mpg Function #
####################

function rm1mpg {
    rm output.mpg
}

####################
# convert Function #
####################

function convert {
    dvdauthor -o dvd -t output2.mpg
}

####################
# rmpg     Function #
####################

function rmpg {
    rm output2.mpg
}

###################
# Rename Function #
###################

function finalize {

dvdauthor -o dvd -T

}

#####################
# ISO Function      #
#####################

function image {

mkisofs -dvd-video -o dvd.iso dvd/

}

#####################
# rm2 Function      #
#####################

function rm2 {

rm -rf dvd/

}


###############
# Script      #
###############

avi ;
rmavi ;
vcd ;
rm1mpg ;
convert ;
rmpg ;
finalize ;
image ;
rm2 ;


exit
```

sudo chmod 755 /usr/bin/avi2dvd

play your avi file into a directory of your choice and cd into it

cd /home/someuser/avidirectory

run this comand

avi2dvd *

it takes about an hour but the end result is an iso to burn using your favorate cd burning software k3b, nero etc

Hello,

I used this great bit of code once before with great success--thanks again.  I'm getting stuck now on one step--"play your avi file into a directory of your choice"--I don't remember how I did this now.  Can you help?

Thanks in advance.

mike

---

### Post by kennyrogersjr on 2009-07-12
**place** your avi file into a directory of your choice...then cd to that directory

---

### Post by mlnease on 2009-07-12
> **kennyrogersjr said:**
> **place** your avi file into a directory of your choice...then cd to that directory

Silly me, I shoulda figured that out--thanks again, krjr.

mike

---

### Post by vinutux on 2009-07-12
DeVeDe...is better option

anyway thankx..................

---

### Post by vinutux on 2009-07-14
> **cindylili said:**
> I often burn the videos such as avi,mpeg,wmv,rmvb etc. to dvd via **[Wondershare Video to DVD Burner]("http://www.ourpix.com/dvd-creator.html#147")**, which is an easy to use dvd creator tool.

itz a windows app not linux

---

### Post by boutch55555 on 2009-07-23
> **rfrayer said:**
> 
```

function rmavi {
    rm *.avi
}

```

This is dangerous... If the script is run from a main download folder, it will delete all avi files. I lost the 5 movies that were on my desktop. Please either chnage it to $1 or remove it completely. Nothing tells you that the user wants to delete the file after the transcoding...

---

### Post by vinutux on 2009-07-23
> **boutch55555 said:**
> This is dangerous... If the script is run from a main download folder, it will delete all avi files. I lost the 5 movies that were on my desktop. Please either chnage it to $1 or remove it completely. Nothing tells you that the user wants to delete the file after the transcoding...

yeh..[COLOR="Red"]**rm** means remove[/COLOR]....

and *.avi means all files contain .avi extension....

---

### Post by rfrayer on 2009-08-11
goodness i simply posted it as a script i use modifie it yourself no use in complaining

---

### Post by phildarski on 2009-11-07
> **boutch55555 said:**
> This is dangerous... If the script is run from a main download folder, it will delete all avi files. I lost the 5 movies that were on my desktop. Please either change it to $1 or remove it completely. Nothing tells you that the user wants to delete the file after the transcoding...

Please do not take this as negativity as I sincerely intend this constructively,  however I feel it's important to note that the only thing that *might* be considered *dangerous* in regards to this post as I can comprehend is the use of the command rm without checking, then double checking, and then, just for extra fun, checking again unless you are certain that you're nuking something you intend to nuke.

We've all deleted needed (or at least wanted) files by mistake  with rm at least once so I'm sure we can all relate to your frustration as you posted this.  Kind of like running a stop sign on an unfamilar road by accident and then getting mad at someone that hits your car.  Realistically you know it's completely your own fault and responsibility not the other driver.  Plus you injured the drivers car.

I agree that keeping the original AVI, for my own personal usage, is more likely although I can think of scenarios where the goal may be to backup avi's to a DVD and clean disk space.

I really appreciate the original poster taking the time to submit this as well as the person that credited him by giving the link to this thread as the script is posted elsewhere now too.

Just as I appreciate the poster for script I'm certain that when you modify the script *yourself using your own suggestions* many others will appreciate your helpful input as well as others may also want to keep the original avi just like yourself.  

I'm sure nobody expects you to say thank you to the poster for his effort under the circumstance. When I do something dumb I get extra mad when I realize I'm the source of my fsck-up.

I'm sure you will have people saying "thank you" for your work if you make the change yourself and post it if you need it function a bit differently. A bit more tacful than telling [rfrayer]("http://ubuntuforums.org/member.php?u=506219") what to do with his script that he shared with all.  

I believe this is more in line with the spirit of this forum and the GPL as well.

Sorry for the  diatribe - I got on a roll and was up all night doing a fresh install (or three).  I tend to go on and on when that happens.  Clearly. :p

Cheers

Phildarski

---

### Post by anthony2010 on 2009-11-13
Hi

Ive been using devede and also dvd styler. Both do what they say but the end result is a jerky picture. The .avi I want to put on dvd plays smoothly on the computer. I'm assuming the software 'shrinks' the .avi and removes frames or something. Is there a way of NOT removing the frames? The .avi is just 700mb so a straight conversion without removing frames should fit nicely on a 4.7 Gb disk?

Any ideas all?

ant.

---

### Post by lechuckpiratesanguinaire on 2010-05-20
I'm using [Dvdtivi lite]("http://www.hitivi.com") under wine to convert Avi to DVD format, but i would like to another GUI under ubuntu.

---

### Post by dirtrider1 on 2011-07-06
I use Mandvd and Devede, both work flawlessly for me when converting avi's to a dvd.iso and then burning with K3b. Honestly I use cli for many thing's but in this case both of those application's make it so easy for just basic/general converting.

---

### Post by haqking on 2011-07-06
In the time it took me to read the post i could of used DeVeDe to do the same thing ;-)

Nice post though ;-)

---

