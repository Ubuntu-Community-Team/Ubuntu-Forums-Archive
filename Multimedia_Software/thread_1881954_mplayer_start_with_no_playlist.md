---
title: "mplayer start with no playlist"
date: 2011-11-16
forum: Multimedia Software
---

### Post by Vich50 on 2011-11-16
Hi,

I am somewhat new to command line, but have been making some progress.  I would be grateful if anyone could help me out with two questions.

Scenario - I have an unattended Ubuntu 11.10 PC.  I have written a script that so far recognises if a usb device is present.  I know how to start mplayer using a playlist, but what I want to do is if a usb device ( e.g. a usb pen ) which contains a series of mp3 files in the root of the usb device, mplayer starts and just plays the contents of the usb device.  Any ideas please?


  On the basis I can get this going I would also like to know if there is a way of directing mplayer audio output via a usb bluetooth dongle to a Creative D200 bluetooth speaker?


  Any feedback would be welcomed.  :)



  Cheers,


  Vic.

---

### Post by andrew.46 on 2011-11-16
Perhaps your script could generate a playlist based on a *find* search of your device? Something like:

```
find <usb-device> -iname '*.mp3' > /tmp/playme.pls
```

This should generate a suitable playlist for MPlayer (and of course '<usb-device>' needs to be your real usb address). Difficult to suggest much more without actually seeing your script :).

---

### Post by Vich50 on 2011-11-18
Hi Andrew,

Thank you for your speedy response.

I do like your suggestion.  I am still working on the script ( when her in doors lets me ).  
So I have put the current script I have, but have not tried it, I am somewhat new to 
scripting and it most probaly shows.  :D

# What this script is trying to achieve is to recognise if a usb pen ( containing a series 
of mp3 files ) is present.  If so then to play those mp3 files.  If there is no usb pen 
present then it will drop through to play ( from a playlist ) mp3 files on the internal 
disk drive.  The second part of the script is two check if a previously present usb pen 
has been removed.  In this case, as above, it will drop through to play ( from a playlist ) 
mp3 files on the internal disk drive.  Then still monitoring the usb slot, if a usb pen is 
inserted, the playlist related to the internal disc drive will terminate and the mp3 files 
on the newly inserted usb pen will play.  

!/bin/bash -x    # watch the script run

while 

do

if mount | grep -G "/dev/sdb1"; then

# device is mounted

# list all the mp3 files to a file named playme.pls in /tmp

find<"/dev/sdb1" >  -iname '*.mp3'>  /tmp/playme.pls

usb-hdd = 1

mplayer  /tmp/playme.pls

else

# device is not mounted

mplayer - playlist musichdd.txt

usb-hdd = 2

fi


#  wait for 60 seconds

    while : 

    do

    sleep 60 

    done

case usb-hdd

1)         if mount | grep -G "/dev/sdb1"; then

        #device is mounted
        
        esac

    else

#device is un-mounted - has been removed - play hdd playlist

        mplayer - playlist musichdd.txt
        
        fi

2)         if mount | grep -G "/dev/sdb1"; then

        #device is mounted
        
        # list all the mp3 files to a file named playme.pls in /tmp

              find<"/dev/sdb1" >  -iname '*.mp3'>  /tmp/playme.pls

        mplayer  /tmp/playme.pls

    esac

done


BTW- I have ordered a Edimax bluetooth dongle and it looks quite straight forward to output the audio to a bluetooth speaker.  I have purchased a Creative D200 bluetooth speaker and I am impressed with the quality of the build and sound.

Cheers,

Vic.

---

### Post by andrew.46 on 2011-11-18
Looks like you have done a fair amount of work on your script already! On small thing: even if the filename is *something.pls* MPlayer still needs the *-playlist* option to recognise a playlist. All the best with the developing script :).

Edit: BTW you need to lose the angle brackets on 'find**[COLOR="Red"]<[/COLOR]**"/dev/sdb1" **[COLOR="Red"]>[/COLOR]** '

---

