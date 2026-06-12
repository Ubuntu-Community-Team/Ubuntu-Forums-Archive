---
title: "MPD (Media Player Daemon) configuration - no audio"
date: 2018-02-08
forum: Multimedia Software
---

### Post by goodstuff9 on 2018-02-08
I have two computer, both running Ubuntu 17.10.  

On computer #1 I installed mpd.  In mpd's  configuration file I have this for audio settings:  

audio_output {
     type        "pulse"
     name        "MPD"
     server      "localhost"
}

On computer #2 I have GMPC (Gnome Media Player Client) running, it is connected to the music database specified in the mpd configuration file on computer #1.  

When I play a song on GMPC on computer #2, it shows the song as playing, but I unable to get any audio to come out of the speakers on computer #1.  When I look at the "Server Settings" under "Preferences" within GMPC on computer #2, in the "Output Devices" section I don't even see the computer #1 output device that I specified in the mpd configuration file on computer #1.  

I've done much searching to figure out what I am doing wrong, but have found nothing.  I am asking if any of you know what I ought to do in order to get audio from the speakers on computer #1 when I am playing music in GMPC on computer #2.

---

### Post by jonnykickinbut on 2018-02-09
I believe your server is pointing to the wrong host. The config needs to be pointing to the correct pulse server in order for the audio to go through to that one, which is on the client machine.  The exact change will depend on the method of communication between the two machines, like an IP address or hostname and see if that works.

I FORGOT TO ADD,  don't forget to make sure to go into the file for pulse, which is default.pa the configuration for pulseaudio and uncomment authorizing connections over the LAN or whatever.  With the following entry should do (if you prefer to restrict access to certain ip address only that is of course permissible).  As is probably several other ways that could still involve pulseaudio or not.  But I just tested this and it works like a charm using the IP address for client in the mpd configuration on server, and then making the following change on the client machine:

/etc/pulse/default.pa
 load-module module-native-protocol-tcp auth-anonymous=true

Another link that could help (if you want to use the preferences in a gui program available as well to pulse)
[https://askubuntu.com/questions/28039/how-to-stream-music-over-the-network-to-multiple-computers](https://askubuntu.com/questions/28039/how-to-stream-music-over-the-network-to-multiple-computers)

---

### Post by goodstuff9 on 2018-02-10
> **jonnykickinbut said:**
> I believe your server is pointing to the wrong host. The config needs to be pointing to the correct pulse server in order for the audio to go through to that one, which is on the client machine.  The exact change will depend on the method of communication between the two machines, like an IP address or hostname and see if that works.

I FORGOT TO ADD,  don't forget to make sure to go into the file for pulse, which is default.pa the configuration for pulseaudio and uncomment authorizing connections over the LAN or whatever.  With the following entry should do (if you prefer to restrict access to certain ip address only that is of course permissible).  As is probably several other ways that could still involve pulseaudio or not.  But I just tested this and it works like a charm using the IP address for client in the mpd configuration on server, and then making the following change on the client machine:

/etc/pulse/default.pa
 load-module module-native-protocol-tcp auth-anonymous=true

Another link that could help (if you want to use the preferences in a gui program available as well to pulse)
[https://askubuntu.com/questions/28039/how-to-stream-music-over-the-network-to-multiple-computers](https://askubuntu.com/questions/28039/how-to-stream-music-over-the-network-to-multiple-computers)



Thank you for your response.  

I had already done everything you discuss in your second and third paragraphs.  That obviously did not help.  

I do not understand your first paragraph.  Your sentences, "I believe your server is pointing to the wrong host. The config needs to be pointing to the correct pulse server...." are mysterious.  Are you able to elaborate, what exactly would I need to change?

---

### Post by tinylagarto on 2018-02-11
I think you have to change this line:

```
[COLOR=#000000]server "localhost"[/COLOR]
```

Put in the the correct hostname or IP address.

---

### Post by goodstuff9 on 2018-02-11
> **ivanovnegro2 said:**
> I think you have to change this line:

```
[COLOR=#000000]server "localhost"[/COLOR]
```

Put in the the correct hostname or IP address.


Well.....  Again, thank you for the ideas.  

I tried "localhost", I tried "127.0.0.1", and I tried the exact internal IP address of the computer.  None of those options worked.

---

### Post by tinylagarto on 2018-02-12
Can your post your .mpdconf. 

Personally I use mpd but just on my main laptop, not as a server.

---

### Post by vanadium on 2018-02-12
Sound is to be fully configured also on computer #1. With gmpd, you are only remote-controlling mpd. Can you get music playing with other software on computer #1, or with an mpd client installed on computer #1?

---

### Post by goodstuff9 on 2018-02-12
> **vanadium said:**
> Sound is to be fully configured also on computer #1. With gmpd, you are only remote-controlling mpd. Can you get music playing with other software on computer #1, or with an mpd client installed on computer #1?

Yes, in all other circumstances sound works just fine on computer #1.

---

### Post by goodstuff9 on 2018-02-12
> **ivanovnegro2 said:**
> Can your post your .mpdconf. 

Personally I use mpd but just on my main laptop, not as a server.

Attached to this reply is my mpd.conf file as you requested:  

[ATTACH]278508[/ATTACH]

---

### Post by tinylagarto on 2018-02-13
Once I had a problem setting up mpd as its own service like in your case and I had problems with the sound because mpd was not in the audio group. 

See what is in the audio group:

```
cat /etc/group | grep audio



```

You can add mpd to it:

```
sudo usermod -aG audio mpd
```

---

### Post by goodstuff9 on 2018-02-13
> **ivanovnegro2 said:**
> Once I had a problem setting up mpd as its own service like in your case and I had problems with the sound because mpd was not in the audio group. 

See what is in the audio group:

```
cat /etc/group | grep audio



```

You can add mpd to it:

```
sudo usermod -aG audio mpd
```


User "mpd" already is a member of the group "audio".

---

### Post by tinylagarto on 2018-02-13
Do you have any error messages or terminal output when starting mpd? It could be useful.

---

### Post by #&amp;thj^% on 2018-02-13
> **goodstuff9 said:**
> User "mpd" already is a member of the group "audio".

See if you can follow this: [https://wiki.archlinux.org/index.php/Music_Player_Daemon#Global_configuration](https://wiki.archlinux.org/index.php/Music_Player_Daemon#Global_configuration)
I found "minidlna" to be a bit easier to setup.

---

### Post by goodstuff9 on 2018-02-13
> **ivanovnegro2 said:**
> Do you have any error messages or terminal output when starting mpd? It could be useful.

Well, not sure if I'm doing this correctly......  

First in a terminal I run mpd --kill

I can see that mpd is not running at this point.  

Then, I run mpd

No other output appears in the terminal.  

I do see that mpd is running.

---

### Post by goodstuff9 on 2018-02-13
> **1fallen said:**
> See if you can follow this: [https://wiki.archlinux.org/index.php/Music_Player_Daemon#Global_configuration](https://wiki.archlinux.org/index.php/Music_Player_Daemon#Global_configuration)
I found "minidlna" to be a bit easier to setup.

When I read through the archlinux instructions, it seemed to me that I was already following those instructions that were applicable to Ubuntu.

---

### Post by tinylagarto on 2018-02-14
> **goodstuff9 said:**
>  

Then, I run mpd

No other output appears in the terminal.  


Then there is no error to report. 

I think I am out because I only configure mpd to run as local user.

---

### Post by pvanryn on 2018-02-14
> **goodstuff9 said:**
> When I read through the archlinux instructions, it seemed to me that I was already following those instructions that were applicable to Ubuntu.

goodstuff are you running MPD as a system service, or a user service? Following [these instructions]("https://help.ubuntu.com/community/MPD"), I set MPD up as a user service and placed my mpd.conf in ~/.mpd.  My audio output looks like this: > audio_output {
             type              "pulse"
             name              "Pulseaudio"
}

I don't bind it to any address.

On my remote client (I use ncmpcpp), I point it to the lan address of my server: > ##### connection settings #####
#
mpd_host = 192.168.1.123
#
mpd_port = 6600
#
mpd_connection_timeout = 5



MPD can be kind of tedious, but once you get everything working right, it the best player around.

---

### Post by tinylagarto on 2018-02-15
Pvanryn posted a great link and there is this I would like to paraphrase from the Ubuntu documentation if setting up as a system service:

> **Bugfix: Giving MPD proper permissions**

[COLOR=#333333][FONT=Ubuntu]Unfortunately, by default MPD does not have the proper permissions to access [PulseAudio]("https://help.ubuntu.com/community/PulseAudio"), the default audio setup on most new Ubuntu systems. If MPD plays for you without these steps, then that's great, but if you can play your songs but no sound is emitted, try the following steps.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]What we need to do is add the user **mpd** to the groups **pulse** and **pulse-access** so that it can access the audio system.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]$ sudo usermod -aG pulse,pulse-access mpd[/FONT][/COLOR]
**MPD starts new pulseserver**

[COLOR=#333333][FONT=Ubuntu]Unfortunatly MPD tries to start its own pulseaudio server. So if you still unlucky you could try:[/FONT][/COLOR]

```
audio_output {
  type    "pulse"
  name    "MPD"
  server  "localhost"   # optional
# sink    "remote_server_sink"  # optional
}
```

[COLOR=#333333][FONT=Ubuntu]Then you need to allow access. You should install paprefs

[/FONT][/COLOR]
```
sudo apt-get install paprefs 

```
[COLOR=#333333][FONT=Ubuntu]Then run it (e.g. alt+f2 and enter paperfs). Click the **Network Server** tab, then check the **Enable network access to local sound devices** box, and finally check the **Don't require authentication** box. At this point make sure to restart the pulseaudio daemon.

[/FONT][/COLOR]
```
sudo service pulseaudio restart

```
[COLOR=#333333][FONT=Ubuntu]Now you should see **MPD** in Sound settings **Application** tab and hear music.

[/FONT][/COLOR]
But like Pvanryn I also recommend and use a user configuration for mpd. It is easier setting up the permissions.

---

### Post by jonnykickinbut on 2018-03-14
I think the main question you have to answer is the one about which set  of speakers is the sound going to be using and then depending on which  computer/audio card that is associated with could influence the method  of connectivity.  Depends whether you want sound as mentioned in the OP to come from the same computer with mpd running, which I think would be much easier (then you are not really streaming anything and just accessing the daemon and playing music from a server).  

There is also this solution for access to the pulseaudio server (over the network)
[https://help.ubuntu.com/community/MPD#MPD_starts_new_pulseserver](https://help.ubuntu.com/community/MPD#MPD_starts_new_pulseserver)

If you haven't installed paprefs it probably would help  ):P

---

