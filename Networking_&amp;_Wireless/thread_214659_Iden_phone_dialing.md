---
title: "Iden phone dialing?"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by dlichterman on 2006-07-12
Hello everyone....

I am wondering if anyone has figured out or can figure out how to make my iden cell phone(i450) dial-able.  If I can make it dial s=2 I can get data access.....its connected via a USB cable.

Thanks,
Daniel

---

### Post by J@F on 2006-08-18
Go to the terminal and type "sudo pppconfig" 

your password 

create a connection

give it a name like boost or nextell, whatever service ur using. (remember this name)

arrow down to "use dynamic dns" then space bar, then enter.

press enter on PAP

for username and password press spacebar

im not sure about the best speed but I put 19200

press enter on tone

the "S=2" thing

I knew my port was /dev/ttyACM0 so I arrowed to no enter. yours should be something with ACM in it look in the /dev directory and look for something with ACM in the name also it changes to ttyACM0 and ttyACM1 with me so i made 1 with ACM0 and 1 with ACM1

arrow down to finished

enter

arrow down to quit

type "pon whatever_the_name_of_the_provider_you_gave_was"

your logged in. just don't keep the phone next to the monitor it will make lines show up on the screen type poff in the terminal when you want to hangup. oh and the i450 can have widen on it and thats 4x faster. hoped this helped

---

### Post by dlichterman on 2006-08-18
I actually found a script somewhere that does it.....Ill try to find the link and post it up

---

