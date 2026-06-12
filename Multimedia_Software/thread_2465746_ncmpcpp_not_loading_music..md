---
title: "ncmpcpp not loading music."
date: 2021-08-10
forum: Multimedia Software
---

### Post by antonio-cpr on 2021-08-10
Hi!
I'm trying to use ncmpcpp but it is no finding my musics neither showing volume icon(Volume: n/a). Is hard to say more precisely what's going on because it doesn't show any error message, just open the software with no music in it.

```
rob@robnote:~$ ncmpcpp 
Reading configuration from /home/rob/.ncmpcpp/config...
```

Here the ~/.config/mpd/mpd.conf content.
```
music_directory        "~/music"
playlist_directory    "~/.config/mpd/playlists"
db_file                "~/.config/mpd/database"
log_file            "~/.config/mpd/log"
pid_file            "~/.config/mpd/pid"
state_file            "~/.config/mpd/state"
sticker_file        "~/.config/mpd/sticker.sql"
bind_to_address        "localhost"
port                "6600"

input {
    plugin "curl"
}

audio_output {
    type        "pulse"
    name        "pulse audio"
}
```
By the way, the "music_directory "~/music"" is in lowercase and it is a symbolic link to /media/backup/music.

Here the ~/.ncmpcpp/config content.
```
ncmpcpp_directory =           ~/.ncmpcpp
mpd_music_dir =                     ~/music
mpd_host =                              localhost
mpd_port =                              6600
mpd_connection_timeout =    5
mpd_crossfade_time =            5


audio_output {
    type        "fifo"
    name        "Visualizer feed"
    path        "/tmp/mpd.fifo"
    format  "44100:16:2"
}

visualizer_fifo_path = /tmp/mpd.fifo
```

When I run "systemctl status mpd.service" I get this:
```
rob@robnote:~$ systemctl status mpd.service
&#9679; mpd.service - Music Player Daemon
     Loaded: loaded (/lib/systemd/system/mpd.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2021-08-10 13:33:52 -03; 6min ago
TriggeredBy: &#9679; mpd.socket
       Docs: man:mpd(1)
             man:mpd.conf(5)
             file:///usr/share/doc/mpd/html/user.html
   Main PID: 10062 (mpd)
      Tasks: 3 (limit: 4143)
     Memory: 12.7M
     CGroup: /system.slice/mpd.service
             &#9492;&#9472;10062 /usr/bin/mpd --no-daemon

ago 10 13:33:50 robnote systemd[1]: Starting Music Player Daemon...
ago 10 13:33:52 robnote mpd[10062]: Aug 10 13:33 : exception: Decoder plugin 'wildmidi' is unavailable: configuration file does not exist: /etc/timidity/timidity.cfg
ago 10 13:33:52 robnote systemd[1]: Started Music Player Daemon.
```
I didn't start this service manually, I runned this command right after the startup system.

And the output of "systemctl --user status mpd.service".
```

&#9679; mpd.service - Music Player Daemon
     Loaded: loaded (/usr/lib/systemd/user/mpd.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2021-08-10 11:28:42 -03; 2h 14min ago
TriggeredBy: &#9679; mpd.socket
       Docs: man:mpd(1)
             man:mpd.conf(5)
             file:///usr/share/doc/mpd/html/user.html
    Process: 5961 ExecStart=/usr/bin/mpd --no-daemon (code=exited, status=1/FAILURE)
   Main PID: 5961 (code=exited, status=1/FAILURE)

ago 10 11:28:41 robnote systemd[1527]: Starting Music Player Daemon...
ago 10 11:28:42 robnote mpd[5961]: Aug 10 11:28 : exception: Failed to bind to '127.0.0.1:6600'
ago 10 11:28:42 robnote mpd[5961]: Aug 10 11:28 : exception: nested: Failed to bind socket: Address already in use
ago 10 11:28:42 robnote systemd[1527]: mpd.service: Main process exited, code=exited, status=1/FAILURE
ago 10 11:28:42 robnote systemd[1527]: mpd.service: Failed with result 'exit-code'.
ago 10 11:28:42 robnote systemd[1527]: Failed to start Music Player Daemon.
```

---

### Post by TheFu on 2021-08-11
Think there is a misunderstanding about directories.

~/ is the HOME directory for the userid that the process runs under.  On Ubuntu, mpd runs under the mpd userid.
The fix is easy, don't point at storage in a HOME directory. Always point at storage that is permanently mounted through an fstab entry.

```
music_directory         "/R/Music"
```

The other change is to allow remote clients to connect (like android or ncmpc or ncmpcpp from other computers), we also need to change the mpd.conf for 
```
bind_to_address         "any"
```

And the last change I had to make was in the 
```
audio_output {
        mixer_type      "software"      # optional
}
```

Just the mixer_type. I didn't touch anything else.

Then you can do an **mpc update** to have mpd scan all the files and build the DB. I think it took overnight for my setup.

I don't use ncmpcpp, so I don't know the specific keyboard stuff for that, but any client can be used to ask mpd to update the library. For example:

```
$ mpc update
Updating DB (#1) ...
volume: 90%   repeat: off   random: on    single: off   consume: on 
```

And just to be clear, don't put ~/ in config files for any daemon. Always to the correct, absolute, path.

Hope this is helpful.

---

### Post by antonio-cpr on 2021-08-14
> **TheFu said:**
> Think there is a misunderstanding about directories.

~/ is the HOME directory for the userid that the process runs under.  On Ubuntu, mpd runs under the mpd userid.
The fix is easy, don't point at storage in a HOME directory. Always point at storage that is permanently mounted through an fstab entry.

```
music_directory         "/R/Music"
```

The other change is to allow remote clients to connect (like android or ncmpc or ncmpcpp from other computers), we also need to change the mpd.conf for 
```
bind_to_address         "any"
```

And the last change I had to make was in the 
```
audio_output {
        mixer_type      "software"      # optional
}
```

Just the mixer_type. I didn't touch anything else.

Then you can do an **mpc update** to have mpd scan all the files and build the DB. I think it took overnight for my setup.

I don't use ncmpcpp, so I don't know the specific keyboard stuff for that, but any client can be used to ask mpd to update the library. For example:

```
$ mpc update
Updating DB (#1) ...
volume: 90%   repeat: off   random: on    single: off   consume: on 
```

And just to be clear, don't put ~/ in config files for any daemon. Always to the correct, absolute, path.

Hope this is helpful.

I made the changes you suggested but unfortunately didn't work. I tried lsof and here the output I got.
```
sudo lsof -i -n -P|grep 6600
systemd      1            root   56u  IPv6  26518      0t0  TCP *:6600 (LISTEN)
mpd        727             mpd    4u  IPv6  26518      0t0  TCP *:6600 (LISTEN)
```

So, searching more on Google I found the following suggestion:
> I'm guessing you've installed the mpd package, that it comes with a systemd unit file, that the unit file is enabled and so systemd has bound the port to do port-based activation. Run sudo systemctl disable mpd.socket (or similar).


I did that and removed mpd from Startup Applications Preferences and now everything is working fine. 
One last thing is I had to add the content bellow in mpd.conf because I was getting exceptions starting mpd.
```
input {
        plugin     "qobuz"
        enabled    "no"
}

input {
        plugin       "tidal"
        enabled      "no"
}

decoder {
       plugin                   "wildmidi"
       enabled                  "no"
       config_file              "/etc/timidity/timidity.cfg"
}
```

---

### Post by TheFu on 2021-08-14
You're running mpd on a desktop?  Ewwww.  Never tried that. Mine are on headless servers, so they have to run as a service.  Additionally, I don't allow IPv6 here.

---

### Post by antonio-cpr on 2021-08-14
> **TheFu said:**
> You're running mpd on a desktop?  Ewwww.  Never tried that. Mine are on headless servers, so they have to run as a service.  Additionally, I don't allow IPv6 here.

Yes on my laptop. Why ipv6 is not allowed I don't know how to configure mine?

---

