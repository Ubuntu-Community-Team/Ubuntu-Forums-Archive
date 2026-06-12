---
title: "Icecast - run multiple instances of Shout"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by Jose Catre-Vandis on 2007-06-04
I have got icecast and shout working fine, but the comments in shout.conf indicate that you can create as many versions of shout.conf (by renaming) as you like with different settings and "mount points", and then run multiple instances of "shout" and therefore offer many different streams for clients to listen to. See extract from shout.conf:
```
# Or, if you plan multiple instances/channels/mount points of shout
# call shout with -C <name> to use a copy of this conf file
# This is so you can have 5 or 500 shout instances running, each with a
# different .conf file, yippee

# mount - is the mountpoint for this stream. Think of this as what channel on 
# the server this stream is for. For instance, you might have several channels 
# on your server, all providing different content.  You might have a rock, rap,
# and # techno channels, or a 56bit and 128bit channel. You would then run a 
# copy of shout for each, specifing different mount's, or channels to reside 
# on. So, you would have http://localhost:8000/rock, http://localhost:8000/rap,
# and # http://localhost:8000/techno, if you specified each copy of shout to 
# use rock, rap, and techno as their different mount points. Got it yet?      <<-No :-)
```

i have no problem in creating a new .conf file with different settings and setting a mount point in my new "shout.conf" (renamed to some thing else) but it refuses to mount/load and if it does will only load the default mount point. Server is on machine 10.10.10.60 (on a 10.10.10.1 local network)

here is my icecast.conf
```

location Here, There and Everywhere
rp_email pop@popplaysthemusic.me.uk
server_url http://popplaysthemusic.me.uk

max_clients 10
max_clients_per_source 10
max_sources 10
max_admins 5
throttle 10.0

use_meta_data 1
streamurllock 0
streamtitletemplate %s
streamurl http://10.10.10.60:8000
nametemplate %s
desctemplate %s

mount_fallback 1

#hackme
encoder_password YAtutg4TIWqEA
admin_password   YAtutg4TIWqEA
oper_password    YAtutg4TIWqEA

touch_freq 5

#hostname disabled

port 8000
port 8001

server_name 10.10.10.60

force_servername 0

logfile icecast.log
accessfile access.log
usagefile usage.log
logfiledebuglevel 0
consoledebuglevel 0

reverse_lookups 1

console_mode 0

client_timeout 30

kick_clients 0

#staticdir c:\windows\desktop
#staticdir /usr/share/icecast/static

templatedir /usr/share/icecast/templates

logdir /var/log/icecast
stats_log stats.log
statshtml_log stats.html
stats_time 60

#alias radiofri http://195.7.65.207:6903 

kick_relays 10

transparent_proxy 0

acl_policy 1
#deny all *
#allow all *.ryd.student.liu.se
```


here is my standard shout.conf
```
server_name localhost
port 8000
password hackme
mount default

name Radio_Pop
desc The_best_pop_music_monkeys_can_buy
genre pop
url http://popplaysthemusic.me.uk
public no

short_titles yes
title_streaming yes
id3 no
autocorrect yes

playlist popplaylist
loop yes
shuffle yes

autodetect yes
default_bitrate 128000
force yes

daemon no
verbose no
```

and here is my second shout.conf named shoutrock.conf
```

server_name localhost
port 8000
password hackme
mount rock

name Radio_Rock
desc The_best_monkey_music_monkeys_can_buy
genre Monkey_Music
url http://rockplaysthemusic.me.uk

public no

short_titles yes
title_streaming yes
id3 no
autocorrect yes

playlist rockplaylist
loop yes
shuffle yes

autodetect yes
default_bitrate 128000
force yes


daemon no
verbose no
```

Commands to get things going:

run server
```
sudo icecast
```
run source client (default)
```
sudo shout 10.10.10.60 -P hackme
```
attempt to run second source!
```
sudo shout 10.10.10.60 -P hackme -C /etc/icecast/shoutrock.conf
```

can anyone please explain how I get these multiple streams set up.

I want to use shout because its simple(lol), and I do not need to do any encoding of files becasue my server will only be used on a lan

---

