---
title: "cant control mplayer with remote or telnet"
date: 2008-02-25
forum: Mythbuntu
---

### Post by rddone on 2008-02-25
My new mythbox 7.10 runs great, but having some problems with the Tira remote. It can navigate around myth just fine, and can play, pause, rew, etc with other players, but when playing movies with mplayer, it is completely unresponsive. It just ignores the buttons completely until the movies has ended.

When I built the new box, I copied the lircrc file from my old 7.04 mythbox which worked fine with the hauppage remote, and have since quadruple checked the file with no issues found. Was there some change in the keybindings or something in relation to mplayer?

On a possibly related note, the telnet control for mplayer was unresponsive on the 7.04 box while playing movies, while the remote worked just fine.

I just dont know where to look to try and determine how to fix this.
TIA, 
Rob

---

### Post by newlinux on 2008-02-25
When you copied the lircrc file over, did you symlink it or copy it to both the home directory of the user running mythtv as ~/.lircrc and ~/.mythtv/lircrc? It  might help to post your .lircrc file...

---

### Post by rddone on 2008-02-25
After much experimentation getting remote to work at all, I had the real copy of the file at ~/.mythtv/lircrc and ignored the ~/.lircrc

I was looking for an unrelated thing and saw a .lircrc file that had a note in it about having the symlink in ~/.lircrc for mplayer to work. I replaced the out of date ~/.lircrc file with a symlink to ~/.mythtv/lircrc but havent been home to verify that it works yet.

Can anyone verify that mplayer gets its Lirc keymappings from ~/.lircrc and all the other programs use ~/.mythtv/lircrc?

Im positive that its not the lircrc files fault that the remote is not working in mplayer since the ESC, stop keys work fine for other progs, and I checked the file several times to be sure that it was mapped correctly for mplayer as well. 

Thanks,
Rob

---

### Post by newlinux on 2008-02-25
Actually, only myth gets config from ~/.mythtv/lircrc and most all other programs get their config from ~/.lircrc (including xine, mplayer, vlc, etc.). So you probably have fixed it.

---

### Post by rddone on 2008-02-25
I wont be able to test the remote with the new 'fix' until I get home, but the remote works fine when playing .mpg files, which get played with a different player. 

I am not sure which player it uses for .mpg, or even how to tell other than checking top when movie is playing.  All I know is the player that works with the remote shows a blue window when trying to pause, ffwd, etc. 

Perhaps the blue windowed player is the player internal to mythtv?

Thanks,
Rob

---

### Post by newlinux on 2008-02-25
You can check (and configure) players on a file extension basis and even at a file by file basis. I use the internal player for almost all filetypes (I like the consistency of interface with my recordings and the ability to bookmark my location in the files). I'm not at my box right now either, but I think the location of the file type association setting is:

Utilities/Setup->Setup->Media Settings->Video Settings->Player Settings or something like that. And you can change the setting for individual files in video manager.

---

### Post by rddone on 2008-02-25
Thanks for all your help. 
Creating the symlink makes mplayer respond to the remote now.
My family is so much happier with me now. 
It was a huge inconvenience to have to go down to the basement to hit escape on the keyboard when deciding to quit watching a moive in progress. 

While trying to figure this out, I toyed with the idea of renaming all of my video files to .mpg to get around the remote control problem, but I am not the kind of person who can just ignore features that dont work correctly. I also like the mplayer interface better since it allows time skipping in different increments, which seems more intuitive than ffwd, wait,play. 

Thanks again,
Rob

---

