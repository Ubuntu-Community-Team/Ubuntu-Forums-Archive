---
title: "External channel change command's presence causes LiveTV to break"
date: 2010-03-25
forum: Mythbuntu
---

### Post by dodongo on 2010-03-25
Hi everyone -- Weird issue here.  I've recently been "encouraged" (i.e., forced) by Comcast to move to using their Digital Transport Adapter.  No worries, I thought, as I have the hardware already, and even thought ahead to purchasing an IR blaster, just in case.

The salient details I can think to mention are this:

1. This is a working MythTV install, and has been for ~4 years or so now!
2. The tuner card works fine.
3. With the tuner card set to channel 4 and the DTA running, I can watch TV just fine.
4. With the situation as in (3) above, I can directly issue the channel change script from the command line, and the unit *responds properly*.
5. Ran chmod 755 [script] and verified all users ought to be able to execute the script.

The variable is this:

When, in mythtv-setup, I have the external channel change command *empty*, MythTV lets me watch Live TV and I can tune to the proper channel manually as in (4) above.

When, in mythtv-setup, I have the external channel change command populated (/usr/local/bin/changechannel.sh), MythTV will not let me watch Live TV.  I select "Watch TV" and the screen goes to the black screen with "Please wait..." for 3-4 seconds, then goes back to the menu.

What in the world do you think is going on here?  I checked the verbose output and nothing seems relevant to me in there.  Please let me know what you need to see to help troubleshoot.

Thanks in advance!

---

### Post by ian dobson on 2010-03-26
Hi,

Does the channel change script actually work (as your mythtv user)? What timeout have you defined for channel change/tune in mythtv? How long does te script take to return/run.

I have a dbox that I use to record several channels (I don't watch much live TV) and it took quite abit to get it working correctly, mainly because MythTV seemed to think the script timed out.

What does your channel change script look like?

Regards
ian Dobson

---

### Post by iponeverything on 2010-03-26
do a "tail -f" on your mythbackend.log and mythfrontend.log and post the output from when you go into live tv.

---

### Post by dodongo on 2010-03-26
All right, thanks again everyone.  I'd like to close the loop on this so that future fools such as I don't have such a problem tracking down the issue.

I don't want to go into details because it's all rather embarrassing (I totally should've known better) but let me say this:  If your symptoms are all of the above:

**Put your channel change script directly in the system path somewhere.  I'd suggest /usr/local/bin.**  Don't be cute and symlink it from somewhere else.  Just don't do it.  You don't want to be writing a tail-between-your-legs post like this yourself.

Good luck!  :)

---

### Post by phroman on 2010-03-26
Wait! Don't be embarrassed, I'm having the same problem and placing my script in /usr/local/bin didn't help.  I totally don't know better...

Please explain what's going on here so myself and others can understand what's going on.  Cheeers :D

---

### Post by dodongo on 2010-03-27
OK, so here's the deal:  Based on how MythTV runs, there's actually a user on your system (generally named 'mythtv') that has to be able to execute the script you want to fire off to change the channel.

In order to test whether or not permissions are set correctly, try the following command from a terminal:

```
sudo -u mythtv /usr/local/bin/[your-script's-name]
```

[EDIT: Feel I should explain what this command is.  sudo doesn't only run a program with root permissions.  With the '-u mythtv' you're actually requesting the command that follows be run as the mythtv user.  This'll emulate what's happening when MythTV tries to change the channel, so you can collect any relevant error messages.]

If for whatever reason your script is in a state that the mythtv user doesn't have appropriate permissions to execute the script, you'll get an error message.

Doing as I did (sequestering the script within my own home directory) there were permissions issues for mythtv to run that script, despite the symlink in /usr/local/bin.

So my suggestion is to give that command a whirl and see what happens!  Good luck!  Do report back when you have the result.

---

### Post by phroman on 2010-03-27
Well, first off, thanks for the quick reply.  The result I get is:  command not found

I get this with 2 different scripts I've tried.  There doesn't seem to be a 'standard' channel change script out there, I've copied these 2 from the forums.  The name of the remote corresponds correctly with my conf file. They're located in /usr/local/bin/  Here are my 2.  

change.sh
> 
REMOTE_NAME=directv
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 

change.pl
> #!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "directv";

sub change_channel {
my($channel_digit) = @_;
system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name $channel_digit");
sleep 1;
}

$channel=$ARGV[0];
sleep 1;
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
system ("irsend -d /dev/lircd1 SEND_ONCE $remote_name ENTER");

This can't be good...   Thanks so much again, standing by....

---

### Post by dodongo on 2010-03-27
OK, gotcha.  So two things:

1.  Did you do anything special to make either of those commands executable?  It would've looked like 'chmod +X [script_name]' or perhaps 'chmod 755 [script_name]'.  If not, try one of those.  Either variant will set the script file's permissions such that any user on the system can execute the file.  If you're doing this directly in /usr/local/bin I think you'll need to add a sudo at the beginning of the command.  Try:

```
sudo chmod 755 /usr/local/bin/[script_name]
```

2.  If you've done 1, then do tell, if you execute either script as yourself or via sudo, do you get a channel change event?  If you do:

```
sudo /usr/local/bin/[script_name] 12
``` does it change the receiver to channel 12?

If not, then I think you're not quite to the same point that I was, and that there are extra steps you might need to take in order to verify that you've properly set up your IR blaster / lirc to transmit the right commands to your TV box.

---

### Post by phroman on 2010-03-27
Allright, I made it executable as root in Natilus, the new response is:
```
joe@mediaserver1:~/Desktop$ sudo -u mythtv /usr/local/bin/change.sh 12
irsend: command failed: SEND_ONCE directv select
irsend: hardware does not support sending
irsend: command failed: SEND_ONCE directv 1
irsend: hardware does not support sending
irsend: command failed: SEND_ONCE directv 2
irsend: hardware does not support sending
irsend: command failed: SEND_ONCE directv select
irsend: hardware does not support sending
joe@mediaserver1:~/Desktop$ 

 

```

here's my dmesg:
```
joe@mediaserver1:~/Desktop$ dmesg | grep lirc
[    5.904095] lirc_dev: IR Remote Control driver registered, major 61 
[    5.912333] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
[    5.912335] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[    5.912353] lirc_dev: lirc_register_driver: sample_rate: 0
[    5.931852] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb7:2
[    5.945847] usbcore: registered new interface driver lirc_atiusb
[   14.788007] lirc_serial: auto-detected active low receiver
[   14.788011] lirc_dev: lirc_register_driver: sample_rate: 0
[   14.788067] lirc_serial $Revision: 5.104 $ registered
joe@mediaserver1:~/Desktop$ 

```

Guessing my system is not correctly seeing my serial port.  It's a pci card which I'm sure is good as it worked a few months ago when I was trying to get mythbunut config'd.  I did all the  dpkg-reconfigure setserial to manual stuff too.  Hmm..  Ideas?

---

### Post by phroman on 2010-03-27
UPDATE:  Working with the direct tv channel change script as found here:
[http://www.pdp8.net/directv/directv.pl]("http://www.pdp8.net/directv/directv.pl")

I cannot run the script from the command line, regardless of parameters or options, I get the error:  Error excessive retries.  And anything in the channel change script fied of the backend still results in no live tv.   Here's my dmesg serial:


```
joe@mediaserver1:~/Desktop$ dmesg | grep serial
[    0.758538] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    6.293835] usbcore: registered new interface driver usbserial
[    6.293866] usbcore: registered new interface driver usbserial_generic
[    6.293867] usbserial: USB Serial Driver core
[    7.655564] tveeprom 0-0050: Hauppauge model 32062, rev B185, serial# 2843044
joe@mediaserver1:~/Desktop$ 
```

Those address settings are the same in the bios. Is this telling me for certain that my serial port is configured and recognized by my system correctly?  As far as hardware, I've got the approved IOGear GUC232A serial/usb adapter to a null modem cable.  Both of which I've used before on a different system so I'm confident they're ok.  Not sure how to proceed.. Thanks for any help.

---

### Post by dodongo on 2010-03-27
Yeah, the irsend failure suggests that lirc is not configured properly.  That's where you need to start.

I'm about to check out for the night, unfortunately...  My suggestion in general (and I mean this not to be dismissive, but rather that I think there is in fact some good guidance available with a little web searching) is to search for lirc configuration / setup for whatever particular tuner (and/or transmitter) you're trying to get to work.

The reason there's no universal channel change script is that *each type of device* to be controlled has its own IR codes corresponding to, e.g., the digits for each channel.  And each transmitting device may have its own set of idiosyncrasies.

Web search is your friend -- it'll give you ideas of how to go about building (ideally through copy-and-paste) the config files you need.

For better or for worse, welcome to hacker-dom, my friend :)

If you post your tuner model info here, someone (or I) might be able to help you track things down....

---

### Post by phroman on 2010-03-27
Dodongo, I can't thank you enough for the kind help.  I've read tons of forum posts from others in the exact same situation as me, unfortunately what fixed their issues isn't working for me quite yet.  I'll definitely be searching for a while, and will report back with a fix, hopefully soon.  Thanks again for the help and assistance, it's much appreciated.  :D

---

### Post by phroman on 2010-03-27
EDIT: moved to end of thread.

 Working with the direct tv channel change script as found here:
[http://www.pdp8.net/directv/directv.pl](http://www.pdp8.net/directv/directv.pl)

I cannot run the script from the command line, regardless of parameters or options, I get the error: Error excessive retries. And anything in the channel change script fied of the backend still results in no live tv. Here's my dmesg serial:


Code:

joe@mediaserver1:~/Desktop$ dmesg | grep serial
[    0.758538] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    6.293835] usbcore: registered new interface driver usbserial
[    6.293866] usbcore: registered new interface driver usbserial_generic
[    6.293867] usbserial: USB Serial Driver core
[    7.655564] tveeprom 0-0050: Hauppauge model 32062, rev B185, serial# 2843044
joe@mediaserver1:~/Desktop$

Those address settings are the same in the bios. Is this telling me for certain that my serial port is configured and recognized by my system correctly? As far as hardware, I've got the approved IOGear GUC232A serial/usb adapter to a null modem cable. Both of which I've used before on a different system so I'm confident they're ok. Does anyone know if the set top box needs to respond in some way, or else that will cause a problem with the script?  Because if the usb port on the back of the receiver isn't functional, that's obviously be a problem. 

This seems to be the error in mythtv backend log:
```
2010-03-28 02:48:34.088 TVRec(1): HW Tuner: 1->1
2010-03-28 02:48:35.246 ret_pid(0) child(2383) status(0x0)
2010-03-28 02:48:36.287 ret_pid(0) child(2383) status(0x0)
2010-03-28 02:48:37.328 ret_pid(0) child(2383) status(0x0)
2010-03-28 02:48:38.370 ret_pid(0) child(2383) status(0x0)
Error excessive retries
2010-03-28 02:48:39.132 ret_pid(2383) child(2383) status(0xff00)
2010-03-28 02:48:39.179 ChannelBase: external tuning program exited with error 255
2010-03-28 02:48:39.221 TVRec(1) Error: Failed to set channel to 4. Reverting to kState_None
2010-03-28 02:48:39.263 TVRec(1): Changing from Watching WatchingLiveTV to None

``` 

Not sure how to proceed.. Thanks for any help.

---

### Post by dodongo on 2010-03-29
> **phroman said:**
> Does anyone know if the set top box needs to respond in some way, or else that will cause a problem with the script?  Because if the usb port on the back of the receiver isn't functional, that's obviously be a problem.

So you're not using an IR blaster for this, but rather connecting the STB to your computer via USB?

I wouldn't _expect_ a response necessarily (if you're doing it via IR of course it's only one-way), but yes, I do wonder if there's not some test you can perform to verify that the STB is expecting a connection in this way.

---

### Post by phroman on 2010-03-29
Who's the King?  Everyone at the mythbuntu forums are, that's who!

  I got it.  Sweet 8lb 6oz baby jesus I got it.  (taladega nights was awesome)  It was of course the simplest thing in the world.  I had read every post in the entire interwebtubes, all the info was there in parts, it just took my concrete slab of a brain a while to put it all together.  I hadn't configured my serial port correctly, once I got it right, everything is fine.  If anyone comes across this and wants info controling a direct tv receiver with mythbuntu, please hit me up.

dodongo, you rock, thanks so much.  I do still see this strange line in my mythbackedlog: I have a separate post here:  [http://ubuntuforums.org/showthread.php?t=1441683](http://ubuntuforums.org/showthread.php?t=1441683)
```
Scheduler, Warning: Listings source '' is defined, but is not attached to a card input
``` 
But my program guide is fine so not sure if I should even worry about it.  Thanks again all!  :popcorn:

---

### Post by dodongo on 2010-03-29
Well that's great news!  Like you, I simply needed the ubuntuforums people to prod me in the right direction for troubleshooting.  Glad it all worked out!

As for that error, it looks like there's probably an entry in the videosource table with a sourceid that isn't present in the cardinput table's sourceid list.  If you care to take a look, running the following SQL query against the mythconverg DB will check this:

```
select * from videosource where sourceid not in
(select sourceid from cardinput)
```

If any rows are returned, that's absolutely the cause of the error.  However, in short, I think it's nothing to be concerned about if things are now functioning as you like.  If the listings are working properly, I think you're fine.

---

### Post by phroman on 2010-03-30
Unfortunately I have no idea how to run an SQL query... )  Ok, off to google.  I'll be back.

---

### Post by dodongo on 2010-03-30
You'll just go to a terminal and run:

```
mysql mythconverg -u mythtv -p
```

Which'll connect you to the mythconverg database using the (-u mythtv) mythtv user and (-p) prompt you for a password.  If you have one.  You may not, but if you do it'll be in mythtv-frontend's settings --> Setup --> General

Then you'll have the little > prompt within mysql.  You can run the following (note that this has changed; add a semicolon at the end to explicitly indicate your command is complete: 

```
select * from videosource where sourceid not in (select sourceid from cardinput);
```

You can have a line break in there or not, doesn't matter.  Semicolon goes at the end and says "I'm done, go run this please."

My results are "Empty set (0.01 sec)".  If you get any rows returned at all, that's the cause of the warning you were receiving, and I don't believe it'll cause you any problems going forth.

Good luck!

---

### Post by dodongo on 2010-03-30
Also this is a good time to note that any command anyone ever tells you to put in the mysql command prompt that starts with anything *OTHER* than 

```
select
```

is probably *making changes to your database* and unless you know very well what's going on with the query, I'd think long and hard about running it verbatim.

---

### Post by phroman on 2010-03-30
Thank you for the heads up on that, I found this sql gui tool, mysql-query-browser, think that's be a good start?

---

### Post by dodongo on 2010-03-30
Ha!  Yeah, it's my preferred method of fiddling with the mythconverg database.  I just gave you the command-line stuff because I think all that installs as dependencies of mythtv / mythbuntu.

So speaking of the GUI now, you can perhaps more intuitively tell at a glance what's going on.  Without turning this into a lecture on relational databases... ;)  The sourceid key in the 'videosources' table also in the 'cardinput' table.  That's what your message is complaining about -- that there's a row in 'videosources' that has a key that is NOT present in 'cardinput'.

I don't know for sure whether the videosources table is used elsewhere in the database, so I can't say for sure whether or not it's safe to identify the renegade entry and delete it.  If it were my system, I might try, but with the understanding that it could mean starting over from (nearly) scratch if I screw it up.  Given that it's YOUR table and it's been a bit of a slog to get to this point, I think I'd recommend ignoring it and just move on :)

---

