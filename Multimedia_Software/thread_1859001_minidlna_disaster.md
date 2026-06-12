---
title: "minidlna disaster"
date: 2011-10-13
forum: Multimedia Software
---

### Post by theone964 on 2011-10-13
Ok first off thanks for even looking at this thread.

I'm trying to install minidlna on my Ubuntu 10.04 desktop to stream media to my Samsung TV and my Xbox 360's. I've been trying to get this to work for the last 3 days now and have tried many things. I've read that there are some problems with the samsung tv dlna but that most people have got the problems resolved.

OK so let me start from the beginning. I installed minidlna 1.0.19 ( at the time i didn't know the version) by adding a ppa from steady6 and then installing it, after a little tinkering with the start up script i finally got it to work perfectly, started up on reboots etc...so i started to watch a 20 minute long show on my TV. It played perfectly then it automatically started playing the next show and i was like this is awesome....about 15 mins into the 2nd show it just stopped and said something about not being able to detect the server of the share doesn't exist. so i came back to my PC and open up System monitor to see all the running processes...sure enough minidlna was not there anymore. I rebooted and minidlna started up mine, this time i fired up the Xbox and played another episode...it played the first episode and then crashed as it tried to load the next episode. one thing i did notice here though however was that while the show got to the 18 min mark i came back to the PC and checked the running process to see if everything was fine but minidlna was not there...so i kinda expected the crash to happen on the xbox when the first episode finished.

So after searching around for a bit io realised i was runnning an old version and maybe by updating minidlan it would fix the problems...ran a sudo apt-get update but kept getting failed messages in reference to the stedy6 source. so i deleted all the files including the startup script from the run levels. then i download the minidlna file from sourceforge.net installed it and now it wont autostart, also my ushare used to start auto start without a single problem but ever since i installed minidlna its not been starting up either. so anyway i fire up minidlna from the terminal and notice that there are 4 processes with the name minidlna and then after a little bit went down to 3, strange i though but everything worked fine. so i fired up the xbox and played a file on there while monitoring the PC. The processes went back upto 4. Waited for the show to finish to see if it started the next one automatically it didn't ( which to me is no big deal at all). but once the show finished the process did go back down to 3

S0 here's what i need help with:
getting minidlna to autostart
maybe getting rid of all the extra minidlna processes
ushare auto starting again

i'm open to completely reinstalling minidlna etc...just tell me how to do it right and it'll try it and post back.

Thank you

---

