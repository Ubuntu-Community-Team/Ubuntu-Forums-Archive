---
title: "3 nm-applets??? Please help"
date: 2007-11-30
forum: Mythbuntu
---

### Post by dannyboy79 on 2007-11-30
i had three nm-applets running in my mythbuntu install. I am using the rt73 from serialmonkey. Since the networking is a /etc/init.d/ service which parses the interfaces file I realized that I didn't even need network-manager because I don't use WPA. All the nm-applets were in the upper right corner of the upper panel. I dealt with it since mythbuntu came out but grew very tired of seeing it. I removed the network-manager-gnome and now I am getting an error once in awhile stating that nm-applet can't continue because of resources aren't there anymore. Can someone tell me how to fix this. I should have grabbed a screenshot of the error but I didn't. the last time the error popped up I was trying to go to site within firefox and the computer kind of froze, even the terminal that I had open, I couldn't close firefox or the terminal. just before pushing the power button to restart the machine, I tried ctrl-alt-f2, and sure enough, there was the command line box thingy. so I entered sudo killall firefox-bin and it shut firefox and there were the 3 errors on top of each other that I couldn't see when firefox was frozen. Internet and networking is still working so I just need to figure out how to get mythbuntu to stop trying to use nm-applet. it's not showing within ps aux and the network-manager isn't installed. Not sure what to do? Any help please.

UPDATE: I think I may have just found it, under Applications, Settings, Autostarted Applications. I have unchecked the nm-applet. Let's see if that does but would like feedback from others. Thanks

UPDATE: I didn't shutdown yet as I am recordings shows currently but the error came up again. I have attached a picture of the error.

---

### Post by dannyboy79 on 2007-12-06
i've waited 5 days. can anyone help me please?

bump

---

### Post by superm1 on 2007-12-06
rm ~/.cache

and then ctrl-alt-backspace

Should take care of it.  Sorry your post got overlooked while I was afk :(

---

### Post by dannyboy79 on 2007-12-06
you don't have to be sorry. You've done great work for mythtv and ubuntu. you've brought the best of both worlds together! great job. thanks for the tip, I'll try it when I get home.

---

