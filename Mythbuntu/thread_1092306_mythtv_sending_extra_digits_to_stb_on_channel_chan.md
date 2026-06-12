---
title: "mythtv sending extra digits to stb on channel change"
date: 2009-03-10
forum: Mythbuntu
---

### Post by nerver on 2009-03-10
Hey everyone,

I've come across a rather strange problem with my mythtv setup (this is actually the last roadblock to a perfectly functioning mythbox that my gf will approve of lol)

I've googled around but can't seem to find any answers for this s I'm hoping someone here might know what's going on.

I have an mceusb remote transceiver that I use to receive signals from my remote and transmit to my set top box and for the most part this works fine. The problem is that sometime on a channel change, either from the remote or using the guide, mythtv will send the digits to the stb, it will change to the correct channel and then mythtv will send 2 extra digits and it will change to a new channel (both mythtv and the set top box change to the new channel)

This happens most of the time when using channels 200 and 222 (although it has happened on other channels as well).

For example:

I go into the guide and select channel 200, mythtv sends 2-0-0 through lirc to my stb and it changes to 200. Then Mythtv changes to channel 20 and send 2-0 to my stb which changes to channel 20. 


Here is the weird part though, this only happens through mythtv on my backen/frontend machine. If I change channels on one of my remote frontends everything is fine and if I change channels with my channel change script from a command line everything works fine. I can see when the lights on my transceiver flashes when sending the correct 3 digits and then there is a pause and it flashes twice more and changes channels again.

Anyone have any ideas?

Thanks,
-Sean

ps this is my current channel change script, I have tried adjusting the sleep values and I added in that initial "sleep 1" on a suggestion from another thread but no go unfortunately:
```
 #!/bin/sh
 REMOTE_NAME=TTV
 sleep 1
 irsend SET_TRANSMITTERS 1
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.8  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME Ok
 exit 0
```

---

### Post by nerver on 2009-03-11
Well, I've sort of narrowed down the problem. It doesn't seem to have anything to do with lirc or my channel script.

It's definately the mythtv frontend that is causing the problem. I plugged in a keyboard and used it to change channels instead of the remote and the same thing occurs, if i type 2-0-0 mythtv recieves it and sends it to lirc to transmit and then after a few seconds without pressing any other keys mythtv seems to think it is recieving 2 more digits and will change channels in mythtv and send to my stb as well.

I have still not been able to replicate the issue when watching tv from a remote frontend. It is only on the combined backend/frontend machine that this occurs.

Would re-installing the frontend on this machine be worth a shot?

Cheers,
-Sean

---

### Post by nerver on 2009-03-31
I just started working on this again, after putting it on the back burner for a couple weeks. It seems that this only occurs while watching live tv. I have lots of recording rules set up now and they  have all worked fine over the last few weeks, none have been on the wrong channel so I'm assuming it is only a problem for watching live tv.

Since it doesn't affect my recordings I'm not too worried about it any more. I rarely watch live tv these days now that my mythbox is working nicely :)

I am still curious though what would be causing this, so if anyone stumbles upon this in the future and has an idea please let me know.

Cheers :)
-Sean

---

### Post by katheleous on 2009-05-02
I experienced a similar issue when setting up kubuntu 9.04 as backend/frontend/desktop system.  The channel change was OK on 2-digit channels, but failed for 3-digit channels. 

I was able to resolve this by removing the inital 1 second delay in my script.  It "feels" like mythtv is only allowing a certain amount of time for the channel to change before deciding the channel change failed.  If you have an initial delay, and a 1 second delay between digits, it is too long for 3-digit channels. 

Script:
#!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "Dish";

sub change_channel {
        my($channel_digit) = @_;
        system ("irsend SEND_ONCE $remote_name $channel_digit");
        sleep 1;
}

$channel=$ARGV[0];
#I HAD TO COMMENT OUT THE BELOW LINE TO FIX THIS ISSUE
#sleep 1;
if (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system ("irsend SEND_ONCE $remote_name select");


If that doesn't work, you may want to experiment with the delays within your script; I had to try for about an hour before I solved my issue.

---

### Post by nerver on 2009-05-04
Hey katheleous,

Thanks for your reply.

I removed the initial 1 second delay from my script and tested it out, unfortunately the issue persists.

I did however find out something new by accident when testing this. I found that if I press 0 and then enter my channel # (doesn't matter if its 2 or 3 digits) then it works every time.. or at least it has so far. I tried approximately 10 channel changes with no issue which is far more successful channel changes than I normally get. This makes it even more confusing :S 

I tried a whole bunch of different timings in my channel script today and they don't make any difference. AT this point I don't think the problem is even with the script. I think it may be a lirc issue possibly, or something to do with having the myth frontend/backend on the same machine

I'm still very confused why myth is sending these extra digits at all though. Especially because I cannot replicate it on any of my remote frontends.

Any thoughts on this katheleous?

Cheers,
-Sean

---

### Post by nerver on 2009-05-04
Well the issue seems to be gone now, which is a plus :)

Looks like it was fixed while I was tinkering with another issue.

The fix apparently was adding the following line at the end of my channel script:

 ```

 ( sleep 5; v4l2-ctl --set-audio-input 1 -d /dev/video0 > /dev/null 2>&1 ) &

```

so my whole script looks like this now:

```

 #!/bin/sh
 REMOTE_NAME=TTV
 sleep 1
 irsend SET_TRANSMITTERS 1
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.8  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME Ok
 ( sleep 5; v4l2-ctl --set-audio-input 1 -d /dev/video0 > /dev/null 2>&1 ) &
 exit 0

```

This was to fix an audio issue I was having with my pvr-150 and when testing this I noticed I was no longer having channel change problems anymore either.

So case closed for now, though I will forever be confused by this lol.

---

