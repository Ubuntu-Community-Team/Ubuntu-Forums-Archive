---
title: "Mplayer GUI"
date: 2008-07-28
forum: Multimedia Software
---

### Post by aisar190 on 2008-07-28
greeting..
i just installed ubuntu on my laptop...dual os thou...im very new to ubuntu...i just installed mplayer....which is quite hard for me...and manage to play streaming video from aznv.tv....but i really appreciate if someone could help me to put gui on this mplayer thinggy...i tried to follow the readme file...but when i try to edit the config file...it says that i dont have permission ? as this thing in root directory...i already change the password for root...but still it keep saying i dont have a permission....can somebody help me solving this issues....as i want to used ubuntu as my primary os.....the internet connection is really fast with ubuntu....its 10x faster....compared to my xp....please help....with simple or step by step guide....as i really dont know what is packages...synaptic stuff...

thx in advance.....

---

### Post by tturrisi on 2008-07-28
The command for the gui is:
gmplayer

---

### Post by gandaran on 2008-07-28
> but i really appreciate if someone could help me to put gui on this mplayer thinggy.

what do you really mean? mplayer has no gui or the firefox mplayer plugin?
how did you install mplayer? synaptic? did you install the mplayer nogui package? if correct then remove it and just install the mplayer package.

---

### Post by aisar190 on 2008-07-28
> **gandaran said:**
> what do you really mean? mplayer has no gui or the firefox mplayer plugin?
how did you install mplayer? synaptic? did you install the mplayer nogui package? if correct then remove it and just install the mplayer package.

i used this....

su root

i entered password

then i wrote this

apt-get install mplayer

after that...its self installed....and only god know where the installer come from....after that i can used it....i dont used synaptic...and...what is synaptic anyway ?

---

### Post by Yannick Le Saint kyncani on 2008-07-28
Hi aisar190,

You should check [http://help.ubuntu.com](http://help.ubuntu.com) for ubuntu basics.

And mplayer is available in the audio/video menu, it's named mplayer something.

Cheers.

---

### Post by aisar190 on 2008-07-28
> **tturrisi said:**
> The command for the gui is:
gmplayer

maaannnnn....thank you sooooo much...really appreciated it....you made my life so much easier...hehehehe.....god bless you mann....

one last thing....how do i edit the \.config file...i need to put some parameter in order to stream the video from [www.aznv.tv....it](www.aznv.tv....it) say i dont have permission to do this....do you know how can i edit this files ?

regards,
aisar

---

### Post by Archmage on 2008-07-28
> **aisar190 said:**
> one last thing....how do i edit the \.config file...i need to put some parameter in order to stream the video from [www.aznv.tv....it](www.aznv.tv....it) say i dont have permission to do this....do you know how can i edit this files ?

You want to edit the /home/(your username)/.mplayer/config

---

### Post by gandaran on 2008-07-28
> after that...its self installed....and only god know where the installer come from....after that i can used it....i dont used synaptic...and...what is synaptic anyway ?
  
synaptic managers every package, you use it to install or remove any package, in ubuntu you can either use the install commands or add/remove or synaptic to install applications.
for a beginner its best to use synaptic than any install commands that you cannot understand.
now can you explain whats happens when you click the option in applications » sound and video » mplayer movie player, does mplayer open with a gui or not?

---

### Post by mali2297 on 2008-07-28
> **aisar190 said:**
> maaannnnn....thank you sooooo much...really appreciated it....you made my life so much easier...hehehehe.....god bless you mann....

one last thing....how do i edit the \.config file...i need to put some parameter in order to stream the video from [www.aznv.tv....it](www.aznv.tv....it) say i dont have permission to do this....do you know how can i edit this files ?

regards,
aisar

Create a directory *.mplayer* in your home directory with the command
```

mkdir ~/.mplayer

```
Then open a new file *config* in this directory,
```

nano ~/.mplayer/config

```
Add the lines that you need, then save (ctrl+o) and quit (ctrl+x).

By the way, it is recommended to use sudo instead of a root account.

---

### Post by aisar190 on 2008-07-28
> **Archmage said:**
> You want to edit the /home/(your username)/.mplayer/config

thanks so much my friend...i already edit the file...and thank you very much..

---

### Post by aisar190 on 2008-07-28
hello martin...really appreciate your help....im not quite understand what is sudo...but the dir already exist in that folder....but from ur suggestion its seem a connection between root and my user directory....thanks anyway...if you keen to explain...im more than happy to read...:)

regards,
aisar

---

### Post by mali2297 on 2008-07-28
> **aisar190 said:**
> hello martin...really appreciate your help....im not quite understand what is sudo...but the dir already exist in that folder....but from ur suggestion its seem a connection between root and my user directory....thanks anyway...if you keen to explain...im more than happy to read...:)

regards,
aisar

You used *su root* above, which makes me think that you have enabled the root account. This is not recommended in Ubuntu, see
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

