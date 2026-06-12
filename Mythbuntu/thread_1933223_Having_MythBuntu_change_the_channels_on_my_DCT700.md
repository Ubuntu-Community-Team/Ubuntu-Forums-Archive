---
title: "Having MythBuntu change the channels on my DCT700"
date: 2012-02-28
forum: Mythbuntu
---

### Post by drewdin on 2012-02-28
I am sooooo close I can taste it!

[https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script](https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script)

So i followed the page above to a T! everything has worked perfect until i get to the part about adding the change-channel.sh to the input connections. see below:

You will need to create a script called change-channel.sh and add it to /usr/local/bin and later add this to the "channel change script" entry in the Input Connections section of "mythtv-setup".

I made the change, saved it to the backend but nothing! where it asks for the Input connections i put  exactly "change-channel.sh", without the quotes of course! is that correct? SHould i put the path to the file also?

Any help would be awesome! thanks again

---

### Post by newlinux on 2012-02-29
The the channel changing script work from the command line? Is it executable?

Yes, try putting in the full path.

---

### Post by klc5555 on 2012-02-29
Make sure also that the channel change script is invoking "irsend" from the correct location when it changes channels. Sometimes these scripts are trying to invoke /usr/bin/irsend when the lirc install has put it at /usr/local/bin/irsend instead. Or the reverse.

---

### Post by drewdin on 2012-04-12
Thanks for the help guys but i ended up getting an HD Homerun prime and that works perfect with MythBuntu so i stopped trying to get the IR working.

---

