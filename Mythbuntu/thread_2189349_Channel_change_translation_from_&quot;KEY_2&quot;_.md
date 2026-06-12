---
title: "Channel change translation from &quot;KEY_2&quot; to &quot;2&quot;."
date: 2013-11-21
forum: Mythbuntu
---

### Post by tegwilym on 2013-11-21
I'm upgrading my DirecTV receiver from an older D770 to a RC64.  I'm forced to since I get the "receiver may be obsolete" message on the screen.  Mythbuntu has been working great for years on this receiver, but the new one is almost there, but I'm stuck. 
I use an irblaster from the serial port to the LED emitter in front of the DirecTV receiver to change the channel.

Here is what is going on:

When I do an:
```
  irsend SEND_ONCE RC64 KEY_4    -->  The channel will change just fine.

```
or
```
  mythtv-channel-change.pl KEY_4   --->  This also changed the channel ok also.

```

But I need to convert that to:
```
   mythtv-channel-change.pl 4   --->  jus the channel number after the channel change script.  But this isn't working when simply using the channel number without 'key' in front. 

```

I did run the  mythbuntu-lirc-generator and did end up with the correct lircrc files in the hidden folders in the home directory.  So I do have those set to translate to what it needs to change the channel, but for some reason it's just not working. 

So here are my codes as they come out from LIST ""

```
irsend: 000000000000001a KEY_YELLOW
irsend: 000000000000001b KEY_BLUE
irsend: 000000000000001c KEY_CHANNELUP
irsend: 000000000000001d KEY_CHANNELDOWN
irsend: 000000000000001e KEY_PREVIOUS
irsend: 000000000000001f KEY_1
irsend: 0000000000000020 KEY_2
irsend: 0000000000000021 KEY_3
irsend: 0000000000000022 KEY_4
irsend: 0000000000000023 KEY_5
irsend: 0000000000000024 KEY_6
irsend: 0000000000000025 KEY_7
irsend: 0000000000000026 KEY_8
irsend: 0000000000000027 KEY_9
irsend: 0000000000000028 KEY_0
irsend: 0000000000000029 KEY_DASH
irsend: 000000000000002a KEY_ENTER

```

How do I just get the commands there without "KEY_" in front of it?  my old lircrd.conf  file from the older receiver worked find but didn't have the KEY_ in front.

I'm assuming that I somehow need to link the lircrc file to it, but just not sure what is missing.

Anyone have some clues what I might be missing or set wrong??

Thanks, 

Tom

---

### Post by novellahub on 2013-11-22
> **tegwilym said:**
> I'm upgrading my DirecTV receiver from an older D770 to a RC64.  I'm forced to since I get the "receiver may be obsolete" message on the screen.  Mythbuntu has been working great for years on this receiver, but the new one is almost there, but I'm stuck. 
I use an irblaster from the serial port to the LED emitter in front of the DirecTV receiver to change the channel.

Here is what is going on:

When I do an:
```
  irsend SEND_ONCE RC64 KEY_4    -->  The channel will change just fine.

```
or
```
  mythtv-channel-change.pl KEY_4   --->  This also changed the channel ok also.

```

But I need to convert that to:
```
   mythtv-channel-change.pl 4   --->  jus the channel number after the channel change script.  But this isn't working when simply using the channel number without 'key' in front. 

```

I did run the  mythbuntu-lirc-generator and did end up with the correct lircrc files in the hidden folders in the home directory.  So I do have those set to translate to what it needs to change the channel, but for some reason it's just not working. 

So here are my codes as they come out from LIST ""

```
irsend: 000000000000001a KEY_YELLOW
irsend: 000000000000001b KEY_BLUE
irsend: 000000000000001c KEY_CHANNELUP
irsend: 000000000000001d KEY_CHANNELDOWN
irsend: 000000000000001e KEY_PREVIOUS
irsend: 000000000000001f KEY_1
irsend: 0000000000000020 KEY_2
irsend: 0000000000000021 KEY_3
irsend: 0000000000000022 KEY_4
irsend: 0000000000000023 KEY_5
irsend: 0000000000000024 KEY_6
irsend: 0000000000000025 KEY_7
irsend: 0000000000000026 KEY_8
irsend: 0000000000000027 KEY_9
irsend: 0000000000000028 KEY_0
irsend: 0000000000000029 KEY_DASH
irsend: 000000000000002a KEY_ENTER

```

How do I just get the commands there without "KEY_" in front of it?  my old lircrd.conf  file from the older receiver worked find but didn't have the KEY_ in front.

I'm assuming that I somehow need to link the lircrc file to it, but just not sure what is missing.

Anyone have some clues what I might be missing or set wrong??

Thanks, 

Tom

Maybe this post will help.  Try changing your channel change script to use KEY_ for the prefix before the number variable is inputted to the script:

[http://ubuntuforums.org/showthread.php?t=1581183&p=10571667&viewfull=1#post10571667](http://ubuntuforums.org/showthread.php?t=1581183&p=10571667&viewfull=1#post10571667)

```
KEY_$digit
```

---

### Post by tegwilym on 2013-11-22
Thanks!  I'll give that a shot.  
I was thinking of something like that, but was wondering if that would work since the receiver takes the channel numbers first, then sends and "enter" or "OK" to change the channel.  But then again, it WILL just transmit the number that I need, now that I think of it.

Thanks for sending that link, that does look exactly like the problem I'm stuck on.  I'll try.
 :-)

Tom

---

### Post by tegwilym on 2013-11-22
(Sorry, this posted twice and I can't find the delete option)




Thanks!  I'll give that a shot.  
I was thinking of something like that, but was wondering if that would work since the receiver takes the channel numbers first, then sends and "enter" or "OK" to change the channel.  But then again, it WILL just transmit the number that I need, now that I think of it.

Thanks for sending that link, that does look exactly like the problem I'm stuck on.  I'll try.
 :-)

Tom

---

### Post by tegwilym on 2013-11-22
Novellahub, 

[SIZE=4]THANK YOU, THANK YOU!!!![/SIZE]

The change worked and my channels are changing, and recording as they should with the new receiver.  I was starting to worry maybe it was time to ditch the Mythtv and go with some "traditional" DVR type machine.  i hated that idea since I've been very proud of this Mythtv machine I built.
No need to follow the sheep yet!

One of the best things about Linux are these forums and the helpful advice people share. 

Thanks again!

Tom

---

