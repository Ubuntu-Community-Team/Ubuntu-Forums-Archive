---
title: "[SOLVED] Weird problem with internet radio and mp3"
date: 2008-10-06
forum: Multimedia Software
---

### Post by Liviu-Theodor on 2008-10-06
I am running ubuntu 8.04 (updated to 8.04.1) and my problem is: I can not play mp3 files after opening an internet radio, and I can not open any internet radio after playing a mp3 file. I can play along mp3 files and youtube files, though, but not youtube and internet radios (the same problems as with mp3s). Is there any way to solve it?

The sound card is integrated, and the motherboard is Foxconn, 945P7MD or 945G7MD model.

---

### Post by Liviu-Theodor on 2008-10-07
Anyone can help? I must say also that I must restart the computer to overcome the problem, just restarting the GUI (<Ctrl>+<Alt>+<Backspace>) does not help. But still, I wish solving the problem for real...

---

### Post by Liviu-Theodor on 2008-10-15
I verified and I have installed both [FONT="Courier New"]ubuntu restricted[/FONT] and [FONT="Courier New"]w32codecs[/FONT]. I updated the programs, and the issue seems to be partially solved.

The problem is occuring with: Audacious, Amarok, Banshee, Movie player, MPlayer, Muine Music Player, Rhythmbox.

But it seems these programs do what I want: GNOME player, VLC media player, Dragon Player.

Now, I will say the problem seem to be related to some programs, not to the sound card. Maybe someone else will have another suggestions, which programs work under the conditions I want?

Edit: I verified: with these two programs, I can play mp3 files after listening an online radio, but I still can not listen to an online radio after playing mp3 files...

---

### Post by stromdal on 2008-10-15
Weird problem. I would suggest trying to killing processes to try to locate which process is causing the problem, but I don't know which ones that would be. Perhaps a more experienced Linux user can help?

---

### Post by Liviu-Theodor on 2008-10-20
I tried to see what processes run in the system, and played a bit with the options of the [FONT="Courier New"]ps[/FONT] command. I really don't know what to look for there. I understand what some of them do, but there are other I have no idea.

---

### Post by Liviu-Theodor on 2008-10-23
I learned (or remembered about the kill command) a bit since my last post in this thread.

So, this command gave me a list of processes:
```
ps -e
```
In there, I thought that mplayer was a good place to start my experiment, as it had listed two or three processes. After running this command:
```
sudo kill <pid1> <pid2> [<pid3>]
```
the problem seem to be solved (just replace <pid*n*> with the real identifiers). So indeed, it were the programs that caused the problems, not the sound card, as they did not freed up the running processes. I think is a good idea to report this bug to ubuntu launchpad. This would be now [https://bugs.launchpad.net/ubuntu/+bug/287963]("https://bugs.launchpad.net/ubuntu/+bug/287963").

---

### Post by stromdal on 2008-10-24
Congrats :-)

---

