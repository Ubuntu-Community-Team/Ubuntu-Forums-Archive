---
title: "Renoise works perfect but no other app has sound!! =["
date: 2010-02-08
forum: Multimedia Software
---

### Post by xfearxnxloathing on 2010-02-08
recently i installed Renoise demo and followed their install instructions from the Renoise 2.1 quickstart guide.  it said if you get any errors to do the following: > Configuring Realtime Threads
If you get a warning message when you start Renoise, read this section.
To allow Renoise to create realtime threads, which are required for low latencies with ALSA or JACK, you have to
edit the /etc/security/limits.conf file. A realtime kernel does NOT help here, it does not set the required options
automatically!
To enable RT thread creation via PAM open the /etc/security/limits.conf file in a text editor as root (or sudo).
Then somewhere near the end of the file add:
YOURUSERNAME - rtprio 99
YOURUSERNAME - nice -10
Replace YOURUSERNAME with your username. You can discover this with the `whoami` command.
Alternatively you could also create a group named “Audio”, add your user to that group, and use “@Audio”
instead of “YOURUSERNAME”.
Save the file. Log Out. Login. At this point it should be working. To verify that it works, launch Renoise,
select ALSA and make sure the “Realtime threads” option is on. You will get a friendly warning like the one above
if RT creation failed. Try again.
 Jack Configuration
 If you don't have "Jack Control (JACK Audio Connection Kit)", we recommend that you install it.
 Jack Control allows easy Audio/MIDI routing with an intuitive GUI. On Ubuntu:
 $ sudo apt-get install jackd qjackctl
 Now you can start it from [Applications] -> [Audio] -> [Jack Control].
Click the "Setup" button, and set following values:
Change the "Priority" value to 89. (If you use realtime kernel, also add check mark beside "Realtime")
Change the "Periods/buffer" value to 3 or more.
In addition, please configure latency and other settings according to the needs of your system.


now i dont have sound where and when i used to, for example: songbird no longer plays sound tho it plays the track and no sound in web browsers aswell, like youtube plays but no sound..  please help!!

*edit  -  has to be something simple because audio for everything was fine until editing that one file and installing that audio jack program.

---

### Post by xfearxnxloathing on 2010-02-09
ok so i shut my comp down upon leaving for the night and when i got home turned it back on it booted up fine and the sound worked.  i dont know the reason why it didnt work so i cant help anyone out if they ever encounter this problem, i guess reboot instead of just logging out and back in.


*update

ok so once again i opened up Renoise and then tried to watch a youtube video and again the same thing, no audio for it yet Renoises audio still worked, i closed down renoise logged out and back in real quick with the ctrl+alt+backspace and still no audio.  im going to have to reboot in hopes that it fixes my problem but then if it works it just means that i'll have to reboot everytime after using Renoise and that sucks, so i still need help please!!!!

---

