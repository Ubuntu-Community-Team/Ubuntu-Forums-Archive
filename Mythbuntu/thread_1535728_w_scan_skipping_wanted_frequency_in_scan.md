---
title: "w_scan skipping wanted frequency in scan"
date: 2010-07-21
forum: Mythbuntu
---

### Post by gc2712 on 2010-07-21
I am unable to scan one channel at my location. Ive tried dvbscan and w_scan with -c AU, but it seems to skip the frequency on which I know there is the channel(s) I am seeking. I was hoping to use w_scan to create an appropriate config file for dvbscan so I can get MythTV with all channels. The frequency I want to scan is:

T 541250000 7MHz 2/3 NONE QAM64 8k 1/8 NONE

I know this frequency is accessible from my STB, the HDTV and also using the same usb tuner in windows XP.

For Info I am seeking SBS in the Cairns region of Australia.

Is there any way I can force a scan of a particular frequency?

---

### Post by ian dobson on 2010-07-22
Hi,

Maybe try w_scan without the c option. Just define the option for your tuner ( -f c or t)

Regards
Ian Dobson

---

### Post by gc2712 on 2010-07-23
> **ian dobson said:**
> Hi,

Maybe try w_scan without the c option. Just define the option for your tuner ( -f c or t)



Tried your suggestion. Unfortunately, w_scan insists on a country code before it will do anything.

Thanks for trying ,I appreciate the help.

---

### Post by ian dobson on 2010-07-23
Hi,

What version of w_scan are you running? From what I remember when I setup my mythtv box I used w_scan with the -f c and the option to create a channels.conf file that is compatible with the mythtv-setup channel scanner.

In my version from w_scan I don't see a -c option

```
 w_scan --help
w_scan: invalid option -- '-'

usage: w_scan [options...]
        -a N    use device /dev/dvb/adapterN/ [default: auto detect]
        -f type frontend type
                What programs do you want to search for?
                c = cable
                t = terrestrian [default]
        -i N    spectral inversion setting for cable TV
                DVB-T: always off
                DVB-C (0: off, 1: on, 2: auto [default])
        -F      use long filter timeout
        -t N    tuning timeout
                1 = fastest [default]
                2 = medium
                3 = slowest
        -k      generate channels.dvb for kaffeine
        -o N    VDR version / channels.conf format
                2 = VDR-1.2.x (depriciated)
                3 = VDR-1.3.x (depriciated)
                4 = VDR-1.4.x/VDR-1.5.x (default)
        -R N    radio channels
                0 = don't search radio channels
                1 = search radio channels [default]
        -T N    TV channels
                0 = don't search TV channels
                1 = search radio TV [default]
        -O N    Other Services
                0 = don't search other services [default]
                1 = search other services
        -E N    Conditional Access (encrypted channels)
                N=0 gets only Free TV channels
                N=1 search also encrypted channels [default]
        -X      tzap/czap/xine output instead of vdr channels.conf
        -x      generate initial tuning data for (dvb-)scan
        -v      verbose (repeat for more)
        -q      quiet   (repeat for less)

and

w_scan version 20080105

```

Regards
Ian Dobson

---

### Post by gc2712 on 2010-07-23
My version of w_scan is 20090808. I did discover that there is an option -I to specify a channels.conf, so I modified one to only contain the frequency I wanted to scan. This worked! But, alas, still no tuning of SBS channel. Don't know what setting I need. I have been using for SBS channel 29 at Bellenden Ker in Cairns, Aust the following:
T 536500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE

Maybe there is an error there in the settings - some of which I don't understand.

---

### Post by hvlugger on 2010-09-15
Not sure what the users problem is, but au-Cairns is installed via dvb-apps in my Ubuntu so I would use this quick command to tune and produce a channels.conf file:

scan $(locate au-Cairns) > channels.conf

Then to make sure I can align the antenna would make sure tzap is installed then copy the channels.conf to $HOME/.tzap and run tzap on one of the channels:

tzap "SBS One" # necessary to be valid entry in channels.conf

Then it's easy to copy channels.conf to your $HOME/.mplayer directory [or link] and run:

mplayer dvb://"SBS One"

To test reception, hope this helps ;)

---

### Post by gc2712 on 2010-09-16
I'll give that a try and report back. Thanks hvlugger

---

