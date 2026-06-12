---
title: "Program to record live stream"
date: 2008-12-03
forum: Multimedia Software
---

### Post by sn0m on 2008-12-03
Hey guys
Does any of you know any programs that records live stream. I'd like to record an hour of internet radio and play it when out jogging in my mp3 player. I tried sound record but the quality is not so good.
Regards
Sokol

---

### Post by pholden on 2008-12-03
I've had no problems using mplayer to record streams, using something like the following:
> mplayer -vc null -vo null -ao pcm:fast:waveheader:file=dump.wav "streamurl"
I then use *lame* to convert the file to mp3 before transferring it to a portable device :)

---

### Post by sn0m on 2008-12-03
than.thanks budy, works a charm.):p

---

### Post by markbuntu on 2008-12-03
streamripper will rip it and soundconverter will convert it.
kstreamripper and soundkonverter for KDE.

---

### Post by andrew.46 on 2008-12-04
Hi,

I see that you have found the answer with MPlayer. If you want to see how obsessive some people can be with recording radio streams have a look at:

[http://andrews-corner.org/ftgws.html](http://andrews-corner.org/ftgws.html)

The obsessed author (ok its me!) is going to add a section to the script soon to manipulate the volume of the generated wav file with SoX.

  Andrew

---

### Post by sn0m on 2008-12-09
Thanks everybody for your help.
This is my first script and I'm feeling quite emotional about it=D>, even most is done by scavenging here and there......
The aim of this script was to record live stream for 2h or so, so I can listen to it when out jogging.
this is the script:

#!/bin/bash

# a simple script to capture 2 hr of tar 
mplayer -vc null -vo null -ao pcm:fast:waveheader:file=tar.wav "http://tar.serverroom.us:9078/" &
# the & sets the job running in the background

sleep 2h

kill $! # kill the most recently backgrounded job

------------------------------------------------------
#convert to mp3
for i in *.wav; do
 if [ -e "$i" ]; then
   tar=`basename "$i" .wav`
   lame -h -b 192 "$i" "$tar.mp3"
 fi
done
#need to clear up
rm tar.wav

#end


linux rocks, is so much fun.
thnx one more time
Sokol

---

### Post by andrew.46 on 2008-12-09
Hi,

Good on you :-). As I mentioned previously I have incorporated some SoX volume modification of the generated .wav file in [my own script]("http://www.andrews-corner.org/ftgws.html#script"). It has made a big difference to the final sound and will allow further modification as I learn a little more about SoX. Would this be of some use in your script?

All the best,

  Andrew

---

### Post by sn0m on 2008-12-10
Hi Andrew thanks for your help.

I have incorporated your suggestion in my script and it looks as follows:

cd ~/my_scripts (i keep them here)

#!/bin/bash

# a simple script to capture 1 hr of aLive in tar
mplayer -vc null -vo null -ao pcm:fast:waveheader:file=stream.wav "http://tar.serverroom.us:9078/" &
# the & sets the job running in the background

sleep 1h

kill $! # kill the most recently backgrounded job
------------------------------------------------------
#improve sound quality and volume using sox
sox stream.wav -n stat > stats 2>&1 || exit 1
VOL=$(grep 'Volume' stats | sed 's/^.*[ \t]//')
sox -v $VOL stream.wav aLive.wav || exit 1
rm stream.wav
------------------------------------------------------
#convert to mp3
for i in *.wav; do
 if [ -e "$i" ]; then
   aLive=`basename "$i" .wav`
   lame -h -b 192 "$i" "$aLive.mp3"
 fi
done
------------------------------------------------------
#need to clear up
rm *wav stats

#end


Script is fine and works a charm if I ./record_aLive

However next it would be to make it run on specific times (mondays and thursdays from 21:00 to 22:00 in cron(I'm new to cron so bound to make silly mistakes.)

therefore crontab -e 
after editing using nano and saving with ctrl o it looks like this:

# m h  dom mon dow   command 
#record alive
00 21 * * mon,thu /home/sn0m/my_scripts/record_aLive.sh

I tried to make the comand run every minute with the configurations */1 * * * */home/sn0m/my_scripts/record_aLive.sh or */1 * * * * ./home/sn0m/my_scripts/record_aLive.sh to see if it works but no joy.
Any idea what I'm doing wrong.
Kind regards
Sokol
I'm new to it, so this what I've done

---

