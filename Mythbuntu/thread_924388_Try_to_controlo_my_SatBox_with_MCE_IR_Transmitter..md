---
title: "Try to controlo my SatBox with MCE IR Transmitter."
date: 2008-09-19
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2008-09-19
I have the same problem i readed in a old post.

I can add that the script work in  the shell, it's just not working with mythtv, when a scroll the guide and i choose a channel it doesn't do anything.

  
> 
Mythtv and IR Transmitter Help
Hello I have been trying to setup a homebrew ir transmitter to change the channels on my STB for MythTv. I have had no luck with the transmitter but it may be due to my lack of linux experience.

I have followed the guide for setting up an external channel changer
[https://help.ubuntu.com/community/My...hannel_Changer](https://help.ubuntu.com/community/My...hannel_Changer)

the last thing I think might fix my problem is the step:

->When configuring your tuner in mythtv-setup, be sure to set the external channel change script to change-channel-lirc.pl

What exactly does this mean? I have entered "change-channel-lirc.pl" into the "External channel changer command:"box of the Input setup in the mythtv setup. Is this correct or am I missing something here?

All in all Myth appears to be working fine but when I change channels nothing happens, I have looked at the ir transmitter though an digital camera when it should be transmitting and there are NO flashes. Is there a way to get my transmitter to transmit on demand for testing purposes?

Any advice would be greatly appreciated.

Thanks, 
I hope u can help me.

---

### Post by anonymousdog on 2008-09-19
It's no a sure solutions, but try the full path to the script and ensure that the backend service account, mythtv by default in Mythbuntu, has rw permission on the file.

---

### Post by impossibilechecisiaquesto on 2008-09-20
Checked the both think,still don't working.

Any others ideas??

---

### Post by tgm4883 on 2008-09-20
You need the full path in the external channel change command.  But first, lets check if the script even works.  Can you change channels from the command line?  syntax would be /full/path/change-channel-lirc.pl #

---

### Post by impossibilechecisiaquesto on 2008-09-20
yes, like i said. the script work and on mythtv imput-connector option i have

/full/path/script.pl

The script is olse myth owned and chmoded to 777 and +x .
 

I think it's a mythtv bug.

---

