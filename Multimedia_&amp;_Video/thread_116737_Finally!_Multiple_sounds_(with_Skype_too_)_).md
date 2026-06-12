---
title: "Finally! Multiple sounds (with Skype too :) )"
date: 2006-01-13
forum: Multimedia &amp; Video
---

### Post by Zhukov on 2006-01-13
Hi there!

Due to the amount of threads out there with how-tos about this i believe it may not work for everyone. So far it worked flawlessly in every machine i've tried!


A lot of this How-to is based on [this excelent one]("http://ubuntuforums.org/showthread.php?t=32063") written by Gandalf :D

You better backup the conf files before edit them, just in case...


```
sudo apt-get install libesd-alsa0
```

```
sudo gedit /etc/asound.conf
```

Now here's the change:
Type this in the file:
```

pcm.asymed { 
         type asym 
         playback.pcm "dmix" 
         capture.pcm "dsnoop" 
 } 
 pcm.!default { 
         type plug 
         slave.pcm "asymed" 
 }
pcm.!dmix {
        type dmix
        ipc_key 1024
ipc_key_add_uid yes
        slave {
            pcm "hw:0,0"
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 48000
        }
        bindings {
            0 0
            1 1
        }
    }
 pcm.!dsnoop { 
         type dsnoop 
         ipc_key 5778293 
         ipc_key_add_uid yes 
         slave { 
                 pcm "hw:0,0" 
                 period_time 0 
                 period_size 128 
                 buffer_size 2048 
                 format S16_LE 
                 rate 48000 
         } 
 } 

```

```
sudo gedit /etc/esound/esd.conf
```

Type this in the file:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

```

gstreamer-properties
```

Now change everything in Audio to Alsa instead of ESD.

Just reboot.

Don't forget to change BMP or Xmms settings to use Alsa. You cant see how to do that in the thread written by Gandalf (link is up there).
The change is in the conf file, Gandalf's didn't worked here.


Dont forget to start skype using:
```
aoss skype
```

---

### Post by LeTon on 2006-01-16
BEE EE AUTIFUL!

Seriously!

I can listen to streaming radios and wach movies at the same time.Great!
I CAN at the same time hear skype calls and whatever callers have to say...but(this is where I hit the dirt) THEY cannot hear me:(.
I think I've tried any possible config...
Moreover I even can hear the mic in may headphones....it works...but nobody hears me over the pond.
Any ideas???? What am I missing?
Please.
Thank you

EDIT: Could it be related with multimedia system selection...I select alsa for input and it hangs the app. on test every time:/

---

### Post by slrafal on 2006-01-16
me too LeTon. I have no idea either what could be wrong?

---

### Post by slrafal on 2006-01-16
LeTon: type alsamixer in a terminal window, and turn up all inputs. It worked for me :)

---

### Post by LeTon on 2006-01-16
They are up.....
I have turned them every possible way, 
:(

---

### Post by swtiro on 2006-01-21
I couldn't find /etc/asound.conf to fix the problem why?

---

### Post by LeTon on 2006-01-21
[QUOTE=swtiro]I couldn't find /etc/asound.conf to fix the problem why?[/QUOTE]

You have to open this with some text editor....in my case it is 
sudo gedit /etc/asound.conf

and then go from there.

I still cant figure out my little problem(see above) .
Anybody???
Please

---

### Post by swtiro on 2006-01-21
Yes, I mean that in the folder  /etc there is no file named asound.conf

---

### Post by LeTon on 2006-01-21
[QUOTE=swtiro]Yes, I mean that in the folder  /etc there is no file named asound.conf[/QUOTE]

Strange. I would not why it is not there, but...you could make it yourself
cd /etc
cat > asound.conf

And then you can edit it...the way you like it.
Hope it helps.

---

### Post by LeTon on 2006-01-21
I get this msg each time I open text editor (gedit) and it seems to be happening with suggested asound.conf
Am I missing something???

ALSA lib pcm_dmix.c:802snd_pcm_dmix_open) unable to open slave

Obviously smth is not quite right.
Please and thank you for your time.

---

