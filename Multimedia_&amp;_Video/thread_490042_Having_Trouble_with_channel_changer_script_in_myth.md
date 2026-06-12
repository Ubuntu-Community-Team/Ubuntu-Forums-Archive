---
title: "Having Trouble with channel changer script in mythtv"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by m1 grant on 2007-07-02
When using mythtv it can change the channel properly to anything above or equal to 100 but not anything below, probably something to do with the script's parsing of myth's arguments i dunno. But whenever I want to watch say 52 or 50 the cable box is tuned to 69 for watever reason and when in the single digits such as 8 I get 181. Any clue what the hell is going on here?

---

### Post by m1 grant on 2007-07-03
bump - please this is keeping me from using mythtv on at least half of my shows

---

### Post by m1 grant on 2007-07-04
bump - someone must be able to help, cmon, or could someone please point me to another channel changing script for mythtv that has worked

---

### Post by wjston on 2007-07-04
> **m1 grant said:**
> bump - someone must be able to help, cmon, or could someone please point me to another channel changing script for mythtv that has worked

It may help you rectify your dilemma if you would give a little more information in your posts. I have been using MythTV and a MyBlaster to change my STB for some time now; however, when I was initially setting up my system, I read numerous posts and, when I needed help, I volunteered as much information as I could think of.

It would help if you could tell the forum viewers exactly what you were trying to control, and what script you are using. Also, you may want to mention what version of Ubuntu you are running and what guide you followed. Unfortunately, there are a number of variables that may or may not be contributing to your problem. One thing I would try is starting mythfrontend in a terminal, try changing channels and then exit and see what errors, if any, were posted in the terminal screen. It  would also be helpful to know which card and remote you are using to control your box.  It took me  almost one year to figure out how to finally get my system to change channels on my satellite box. Keep posting, but provide as much info as you can.

---

### Post by m1 grant on 2007-07-04
K well, I am using the ubuntudocs channel changing script. Everything else in mythtv seems to be working smoothly, other than this problem.

 I wrote my own script to see what numbers were being fed to the channel changing script to see if the script was to blame, and it seems it isn't because, for all 2 digits channels that have been tried so far (50,52,71) I get large strings of numbers starting with either 68 or 69. 

It also seems interesting that all the channels that are screwing up (channels <100) also are imporperly labeled as Adding Channel xx (xx for channel number). I don't know if this is to blame but it seems more than coincidence. And on that note, why don't these channels get properly labled as the other several hundred are?

I doubt it matters but I am using the windows media center remote kit to transmit IR to the STB and using its corresponding mceusb2 module in lirc.Ive tested lirc multiple times using irsend and it has no trouble transmitting any number or the command enter. 

Im running feisty with the latest version of mythtv from the stock ubuntu repositories. 

I honestly can think of any more relevant info, so please help.

---

### Post by m1 grant on 2007-07-04
o yes and i have also seen that the stb is proprly receiving the wrong channel numbers. When 8 is entered i see 181 appear on the STB's display and for 50 52 and 71,  68 69 69 show up respectively

---

### Post by wjston on 2007-07-05
> **m1 grant said:**
> It also seems interesting that all the channels that are screwing up (channels <100) also are imporperly labeled as Adding Channel xx (xx for channel number). I don't know if this is to blame but it seems more than coincidence. And on that note, why don't these channels get properly labled as the other several hundred are?

I am assuming that you are using Zap2it listings to fill your guide info. Are all your channel listings set up properly here? If so, (also are imporperly labeled as Adding Channel xx (xx for channel number)) - sounds like MythTV has not picked up these stations when it runs mythfilldatabase. Did you set your card up properly - choosing the right channel frequency?

I would go to your Zap2it listings and uncheck any channels you don't need and ensure all channels you normally get are checked. Also, if you run irsend xx (x-channel #) in a terminal, does that change the channels properly?

---

### Post by m1 grant on 2007-07-05
well is channel frequency relevant when I'm grabbing AV off of the STB? If so how do you go about doing that? And yes I have done a lot of testing of the irsend commands, it sends whatever number you tell it to, to the STB properly.

I will try and play around with zap2it tonight to see if that fixes anything.

---

### Post by wjston on 2007-07-06
> **m1 grant said:**
> well is channel frequency relevant when I'm grabbing AV off of the STB? If so how do you go about doing that?

MythTV uses the channel frequency to tune into your signal. 


>  And yes I have done a lot of testing of the irsend commands, it sends whatever number you tell it to, to the STB properly.

If your channel changes correctly outside MythTV, using irsend, then it is MythTV that is not communicating correctly with your STB. It may be your remote or the position of the ir receiver that is communicating with the STB.

---

### Post by m1 grant on 2007-07-06
yes but i am using Svideo in and audio in to grab my tv feeds not the coaxial input, so I dont understand what frequency has to do with anything, unless it also has something to do with the datadirect listing.

---

### Post by m1 grant on 2007-07-06
and fixing the zap2it listing didnt help, I asked to redownload a cleaned up zap2it listing both in mythbackend setup and mythfilldatabase and I still have the same problem. Can anyone tell me why when I wrote this script inplace of the channel changing script I am recieving strange numbers such as 69252007 for channel 52, and 18122007 for channel 8, while getting no problems whatsoever for channels 100 and up.

troubleshooting script for mythbackend setup

```

#!usr/bin/perl
$channel=$ARGV[0];
system (printf "MYTHBACKEND CHANNEL OUTPUT");
system (printf $channel);

```

---

