---
title: "URGENT! need major help!! may have killed computer"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by BXA121 on 2008-03-03
tried to install real media codecs - it was ok with one guide, but the video playback was really slow. 

i decided to try a different guide found here:

[http://www.linuxquestions.org/questions/linux-software-2/help-with-ubuntu-7.10-64b-playing-media-files.-602617/](http://www.linuxquestions.org/questions/linux-software-2/help-with-ubuntu-7.10-64b-playing-media-files.-602617/)

i simply thought "oh cut an paste jobby" 

i cut and pasted this into command. 

the script was so small i didnt realise.  ( i have gutsy)
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

the next command was
sudo apt-get update

i didnt work. i got an error: 

E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

so i edited the file with sudo gedit and put a hash # on the front line,

i then realised it was a feisty command and so i changed the command and slotted gutsy into where fiesty was. 
that command worked fine. 

but update didnt
it came out with a error on line two.   

E: Type &#8216;<html&#8217; is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list


i decided to back peddle. 
i went into tho synaptec manager and deleted the medibuntu respository and key. 

i got a different error:
"E: Type &#8216;<html&#8217; is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report."


none of this helped. 

now my computer wont update and ive killed one of a few quite important things. how do i fix this guys?

:confused:

---

### Post by taurus on 2008-03-03
Just remove it.

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by BXA121 on 2008-03-03
ok i did the above. 
thanks man. 
i used this guide

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

reinstalled gutsy medibuntu repos.

how do i get the medibuntu repo back into synaptic manager?

thanks for all your help!

---

### Post by taurus on 2008-03-03
Just click the Refresh button or from a terminal, run the update.

```
sudo apt-get update
```

---

### Post by BXA121 on 2008-03-03
woohoo! 

man your a star! 

i got my repo back! 


yay!



ok so armageddon averted. 
guess i have to figure my realmedia playback in a safer way. 


thanks for all your help man!

---

