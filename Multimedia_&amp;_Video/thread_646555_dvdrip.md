---
title: "dvd::rip"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by triplemaya on 2007-12-21
I guess this is a confession that I am terminally stupid, but I cannot work out how to use dvd::rip. I have read the docs, endlessly, and I have looked at all the post here on the ubuntu forum, but evidently no one is a stupid as I am! I have even made it work once a few months ago, but now I come to try to use it again it is impenetrable.

I open a new project, but there is no button which will activate the rip. I am at my wits end. Please would someone lead me by the hand and tell me how to use it.

I even tried to ask a  question on the newsgroup, but although I joined the newsgroup I can not find any kind of link to post a question. this whole things seems to be for experts out of my league!?

---

### Post by dannyboy79 on 2007-12-21
if I remember correctly, dvd:rip just opens, then you hit new project and if you had a dvd in the dvd drive that isn't encrypted with newer technology than it should just appear. you chose which titles you want to rip, then after that you select transcoding options.

Here's what it says at this website: [http://www.bunkus.org/dvdripping4linux/single/index.html#ripping_dvdrip](http://www.bunkus.org/dvdripping4linux/single/index.html#ripping_dvdrip)


3.3. ...using dvd::rip
dvd::rip can do the same job for you.
Fire up dvd::rip by typing dvdrip. You'll see the main window. Chose Edit / Preferences and dvd::rip will come up with the preferences dialog. Here you'll have to enter your paths. The first is the path to the DVD device and not the mount point. Often it is /dev/dvd which is a symlink to the real device, e.g. /dev/hdc.
Close that dialog. Now start a new project (File / New Project). It will start with the storage tab. Again enter the correct paths. Note how the other name fields change when you change the project title.

Change over to the Rip Title tab and press the Read DVD Table of Contents button. After a second or two the list below will be populated with the titles that are stored on the DVD. Just select the title you want to rip (you can select multiple titles by holding CTRL and clicking on them). Chose the language and the angle. Leave Specify Chapter Mode on No. Last step: press Rip selected Title(s)/Chapter(s). Again be patient. Drink some milk. Have a nice chat with your girlfriend.

The rest of dvd::rip will be covered later in chapter 4.

---

### Post by triplemaya on 2007-12-21
Many thanks, that's just what I needed. Happy Xmas!

---

