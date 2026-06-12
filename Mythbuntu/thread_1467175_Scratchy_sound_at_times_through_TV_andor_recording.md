---
title: "Scratchy sound at times through TV and/or recordings"
date: 2010-04-30
forum: Mythbuntu
---

### Post by tegwilym on 2010-04-30
I had this same problem with Mythdora 5 which I had been using up until recently when I finally got Mythbuntu running well - now I have to go up to .23/10.04.
Anyway, every now and then I'll get kind of strange sound - distorted, kind of scratchy sounding audio on the high frequency end of things.  I can hit 'esc' to stop the live TV then go back in again and it will be fine.  The problem is when I'm recording and it does that, the recording will be totally screwed up and horrible sounding since I wasn't there to 'esc-restart' to clear it. 

So, when I was on Mythdora 5, I posted a message about this and found a solution that worked.  (please see thread here - [http://mythdora.com/?q=node/3669](http://mythdora.com/?q=node/3669))
Basically, I would us a cron job that would run this script every 60 seconds.  So if a recording/live TV started out sounding bad, it would pop it back if I just wait 1 minute until the script executed and all was fine after that.  It still runs every minute, but didn't do anything unless the sound was bad. 
This is the code:
```
 #!/bin/bash
sleep 3
/usr/bin/v4l2-ctl -c audio_emphasis=0

```
My new Mythbuntu did the same thing last night, so I tried the code, but the /usr/bin/v412-ctl file wasn't there to run.

Anyone know what the equivalent would be in Mythbuntu so I can get this thing kicking my audio again?

Thanks in advance!

Tom - 99% Windows Free home. :)

---

### Post by tgm4883 on 2010-04-30
Take a look at [http://www.mythtv.org/wiki/Ivtv_Channel_changer](http://www.mythtv.org/wiki/Ivtv_Channel_changer)

---

### Post by tegwilym on 2010-04-30
> **tgm4883 said:**
> Take a look at [http://www.mythtv.org/wiki/Ivtv_Channel_changer](http://www.mythtv.org/wiki/Ivtv_Channel_changer)

Thanks for the link.  That could be something, either 'esc' or change channel back and forth will get the sound to change to normal.  I didn't mention that I'm running the Hauppauge PVR-150 capture card which has worked very well.

So if I ran this code with a cron job it should fix this?  

```
#!/usr/bin/perl
system "directv.pl port /dev/ttyS0 $ARGV[0]";
system "v4l2-ctl -d 2 --set-audio-source=2";
my $pid = fork;
if ($pid == 0) {
  sleep 3;
  system "v4l2-ctl -d 2 --set-audio-source=1";
  exit(0);
}
```

Tried it, and didn't see any errors or anything, but I'm at work running an ssh connection to my home machine right now.  I'll have to test it when I get home. 

Tom

---

### Post by tgm4883 on 2010-04-30
No don't run that with a cron job. That would be a bad idea.

Take the code from the page I provided and add it to a file called myth-chan.py, then use that as your channel changing script.

---

### Post by tegwilym on 2010-04-30
Yeah, the cron I had before was running all the time, but it didn't seem to hurt anything.  Running it during a channel change does make more sense.  I think I had problems with it running correctly before when I tried with Mythdora, so I did a cron for it.

This is what I'm using for the channel changing script.  I just use a serial IR blaster to change the channels, and the wireless keyboard is my remote.  

```
#!/bin/sh

# original setting ----- REMOTE_NAME=gi-motorola-dct2000
REMOTE_NAME=sat
cmd="$1"

case $cmd in
    [0-9]*)
    for digit in $(echo $1 | sed -e 's/./& /g'); do
        irsend SEND_ONCE $REMOTE_NAME $digit
        sleep 1
        # If things work OK with sleep 1, try this for faster channel changes:
        # sleep 0.3
    done

# Below command to send a [enter] command --- Tom
#irsend SEND_ONCE $REMOTE_NAME enter    <---Enter or whatever to change the channel ---TOM
irsend SEND_ONCE $REMOTE_NAME ok
    ;;

    *)
        irsend SEND_ONCE $REMOTE_NAME $cmd
        ;;
esac
```

---

### Post by geekyhawkes on 2010-05-01
Your problem sounds fairly similar to mine here;

[http://ubuntuforums.org/showthread.php?t=1456644](http://ubuntuforums.org/showthread.php?t=1456644)

Did you adding the audio_emphasis=0 fix the clicking/scratching issue?  Im new to this part of the setup, what exactly is the script changing within the setup? How does it fix the audio?

Thanks

---

### Post by tgm4883 on 2010-05-01
It seems to be a bug in the IVTV driver. Take a look at the following bug report and also the attached mythtv bug

[https://bugs.edge.launchpad.net/mythbuntu/+bug/210852](https://bugs.edge.launchpad.net/mythbuntu/+bug/210852)

---

### Post by tegwilym on 2010-05-01
The link that TGM posted above does look like the same thing I have going.  I've used the new 9.10 version for about a week and it happened once so far, so I think it's not as bad as with the Mythdora 5, but still there.
I haven't tried the code you sent yesterday, but will get at that today and see what happens.

Tom

---

### Post by tegwilym on 2010-05-01
> **geekyhawkes said:**
> Your problem sounds fairly similar to mine here;

[http://ubuntuforums.org/showthread.php?t=1456644](http://ubuntuforums.org/showthread.php?t=1456644)

Did you adding the audio_emphasis=0 fix the clicking/scratching issue?  Im new to this part of the setup, what exactly is the script changing within the setup? How does it fix the audio?

Thanks

That seems different.  I don't get clicking, just a really 'tinny' sounding audio on the high frequencies. Flipping channels or 'esc' and 'watch tv' again will usually fix that.

---

