---
title: "Controlling Rhythmbox via ssh"
date: 2010-04-11
forum: Multimedia Software
---

### Post by avongil on 2010-04-11
I just want to skip a song or increase the volume on the song that is playing via SSH so I don't have to get up and do it on the remote computer.

so I have figured out how to do this from this guys post: 
[http://xuedi.de/blog/2010/04/08/remote-control-rhythmbox/](http://xuedi.de/blog/2010/04/08/remote-control-rhythmbox/)


basically 

to control rythembox remotely to this:

make alias to the remote machine:

alias rc='ssh yourusername@192.168.1.103 env DISPLAY=:0.0 rhythmbox-client --no-start'

then use commands with new RC alias.  Works but you have to specify a pass every time.


rc --next
rc --volume-up
etc...


Availible Commands:

  -h, --help                 Show help options

Application Options:
  --debug                    
  --no-start                 Don't start a new instance of Rhythmbox
  --quit                     Quit Rhythmbox
  --no-present               Don't present an existing Rhythmbox window
  --hide                     Hide the Rhythmbox window
  --next                     Jump to next song
  --previous                 Jump to previous song
  --notify                   Show notification of the playing song
  --play                     Resume playback if currently paused
  --pause                    Pause playback if currently playing
  --play-pause               Toggle play/pause mode
  --play-uri=URI to play     Play a specified URI, importing it if necessary
  --enqueue                  Add specified tracks to the play queue
  --clear-queue              Empty the play queue before adding new tracks
  --print-playing            Print the title and artist of the playing song
  --print-playing-format     Print formatted details of the song
  --set-volume               Set the playback volume
  --volume-up                Increase the playback volume
  --volume-down              Decrease the playback volume
  --print-volume             Print the current playback volume
  --mute                     Mute playback
  --unmute                   Unmute playback
  --set-rating               Set the rating of the current song

----
Works check out the example command.

alvaro@GNU8710w:~$ rc --print-playing
alvaro@192.168.1.103's password:                <--- this stinks though
Megadeth - A Tout Le Monde


My question is this:

Is there an easier way? Is there a trick to login in to the remote computer so it works?  
This way I posted works but you have to enter your password every time. 

Any thoughts on how to make this more painless?

Thanks.

---

### Post by Lewix7 on 2010-04-12
I believe you can use a key to log in instead of your password; that way whenever you log in to your remote computer, it'll check the key instead of asking you for your password.

To do that you first need to generate a pair of keys on the client computer (you can use rsa or dsa as you like):

```
ssh-keygen -t rsa
```

That should generate a pair of keys in your ~/.ssh folder. Next you'd want to copy the public key (~/.ssh/id_rsa.pub if you used rsa) to the ~/.ssh/authorized_keys file on the remote computer. You can use ssh-copy-id to do it automatically.

```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@ip
```

Afterwards you should be able to connect to the remote computer with ssh without having to enter your password.

Note that if you used a passphrase when your generated your keys, it'll ask you for that every time...

```
ssh-add
```

Enter your passphrase and it should remember it next time.

---

### Post by dannyboy79 on 2010-04-12
i would say yes, install x11vnc, if it's just a local network and you have a firewall/router then it wouldn't matter (and also not over wifi). you could just remotely enter the already running session on the computer that's running rythmbox, do what you want from the computer your sitting at. i do it all the time from work. but i do this over a tunneled ssh session. i vnc back into the already running session back hoome and it's like i've satten back down in my chair at home! awesome.

---

### Post by avongil on 2010-04-13
Both great options. 

I was thinking, could I do it with a shell script?  for example :

remotecontrolscript -vu  and that would run the volume up command and then auto insert my pass? Just by storing a plain text pass in the shell script?

I was just wondering if there was a simple solution to do this from the client without messing with the remote computer.

---

