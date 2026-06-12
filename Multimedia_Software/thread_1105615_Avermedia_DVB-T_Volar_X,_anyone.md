---
title: "Avermedia DVB-T Volar X, anyone?"
date: 2009-03-24
forum: Multimedia Software
---

### Post by t0p on 2009-03-24
I'm planning to get a TV card/stick for my computer, so I can watch the freeview channels - I don't own a TV.

I'm going to get the device from [Maplin]("http://www.maplin.co.uk"), as there's a branch just down the road from my home.  Of all their TV sticks and cards, I think the [Avermedia DVB-T Volar X]("http://www.maplin.co.uk/Module.aspx?ModuleNo=221083") is the one I need.  It's the only one that mentions Linux in its description: the FAQ says:

>  Q) Is it linux compatible?   - Arran

A) Works fine with Fedora Core 6 and Myth TV (cannot confirm any other distributions) 

Before I shell out for this equipment: has anyone got any experience of using it with Ubuntu?  Or any distro?

---

### Post by scottishnarn on 2009-03-29
I fell for this as well. DON'T buy this card, it doesn't work under linux. Or rather it only works with one specific vey old kernel. I think Aver released a closed source driver for one kernel and haven't done anything since.

---

### Post by garhol on 2009-06-12
I'm running the usb volar x with kernel 2.6.28-11-generic (Jaunty).
No problems at all with MeTV. I'm currently working on getting the remote working but it's fine for playback and recording (recorded Derren Brown last with no glitches).

I had it working last year in both Kaffeine and MeTV but after a kernel update it did break. I never got round to recompiling but when I plugged it in two nights ago and it worked straight away with nothing other than a new scan for channels.

I would have agreed with scottishnarn as until recently I figured it was bit of hassle to recompile all the time but it seems that someone somewhere fixed something :)

---

### Post by t0p on 2009-06-19
Thanks, scottishnarn and garhol.  Since posing this question, I have acquired a TV so I'm not going to get this kit any time soon.  But it's nice to know that it works.  It's also nice that someone was prepared to answer!

---

### Post by rusty377 on 2009-07-06
garhol or anyone with info,

I am new to Ubuntu but just recently purchased Aver Volar MAX. I have successfully installed the driver but cannot get Volar to work with any programs. I have tried both Kaffeine and Me TV without any luck. Any suggestions for a newbie?  I am using Ubuntu 9.04


I really want to be able to record from VCR to convert tapes to digital mainly.


Thanks and cheers,

Rusty

---

### Post by garhol on 2009-07-06
Hi Rusty, I'll offer what help I can.

The Volar Max looks pretty similar to the DVBT stick that I am using.
I think that the first thing to do is to try and get the Volar Max working with a standard tv signal then look at vhs input.

I found that the biggest problem I had intially was setting up the channels for the stick as I need to find the transmitter.
I have installed dvb-apps and libdvbpsi3 at some point during the process and dvb-apps is needed to get the tool "scan" which searches out channels for you.

There is a nice tutorial on setting up freeview here which details the steps needed to scan for channels.
[http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/](http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/)
For my setup I used:
```
garhol@Ubuntu-Desktop:~$ tail  /usr/share/dvb/dvb-t/uk-Tacolneston
# UK, Tacolneston
# Auto-generated from http://www.dtg.org.uk/retailer/dtt_channels.html
# and http://www.ofcom.org.uk/static/reception_advice/index.asp.html
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
T 810000000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
T 786000000 8MHz 2/3 NONE QAM64 2k 1/32 NONE
T 730167000 8MHz 2/3 NONE QAM64 2k 1/32 NONE
T 769833000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
T 794000000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
T 818000000 8MHz 3/4 NONE QAM16 2k 1/32 NONE

```
Easiest thing to do is to google your local transmitter and post it back if you are having probs getting the setting you need for your transmitters conf.

From the home dir
```
sudo scan /usr/share/dvb/dvb-t/uk-Tacolneston > channels.conf
cp channels.conf .mplayer/
mplayer dvb://"Channel 4"
```
Bingo. Ouput from a channel. Stage 1 complete.

Can you try running through those steps on the davidwinter site and see where you get to? I think that will be the quickest way of seeing if the stick will work with your system properly.

Let me know where it breaks and how and we can have a look and see where it's going wrong and (hopefully) get it sorted.

---

### Post by rusty377 on 2009-07-07
garhol

Thanks for the reply- appreciate it. I downloaded the driver from Avermedia and installed it and it also came with some "tools" in a folder "H826D Tools" with programs like set-std, tv-player, xtv, vbi-cc and open-file. All are executables but do nothing when I click on them. I did do a terminal session and go inside that folder and type make with some results (like recreating the above files). Is there anything akin to "installing" these programs or should they just run? When you click on them nothing happens.


Here is the contents of the "Makefile" in that folder:
---------------------------------------------------------------------------------------------
CFLAGS=-O2 -Wall -g -D_FILE_OFFSET_BITS=64 $(EXTRA_CFLAGS)

LNK:=aver
X_OBJ:= xtv.o vbi-cc.o 
C_OBJ :=tv-player.o radio-player.o set-std.o probe-v4l2.o open-file.o
TARGET:=${C_OBJ:.o=}
TARGET+=${X_OBJ:.o=}

all : $(C_OBJ) $(X_OBJ)

$(C_OBJ): %.o : %.c
	$(CROSS_COMPILE)gcc $(CFLAGS) -o $* $<

XLIB_PATH := $(shell locate libX11.so 2>&1 | grep libX11.so | tail -n 1 | sed -e 's/\(.\)libX11.so/\1/g' | sed s/\[.][0-9]//g)
usrX11R6 = $(shell test -e /usr/X11R6/lib/libX11.so && echo 1 || echo 0)
usr = $(shell test -e /usr/lib/libX11.so && echo 1 || echo 0)

ifeq ($(usrX11R6),1)
$(X_OBJ): CFLAGS+=-L/usr/X11R6/lib/
else
  ifeq ($(usr),1)
        $(X_OBJ): CFLAGS+=-L/usr/lib/
  else
        $(X_OBJ): CFLAGS+=-L$(XLIB_PATH)
  endif
endif

$(X_OBJ): %.o : %.c
	$(CROSS_COMPILE)gcc $(CFLAGS) -o $* $< -lX11 -lXext -lXv

.PHONY: clean

clean:
	rm -f $(LNK) $(TARGET) $(C_OBJ) $(X_OBJ) *~ 

-------------------------------------------------------------------------------------------
I don't know yet how to check log files- but I will keep trying :0)


Thanks and cheers,

Rusty

Come to find out the programs are all run from terminal shell. I have actually used the software to configure Volar MAX to select composite input and can play video files from VCR using the TV-Time program even though MAX only supports 16 bit video (in their tools programs anyway)- that's progress for me :0)

Cheers,
Rusty

---

### Post by adm1968 on 2009-10-31
[FONT="Georgia"][SIZE="3"]Funny problem over here with this gadget!
Got it to work out of the box with 9.04
No way to make it work under 9.10
(it does get detected)

Anybody knows what is wrong with this and Karmic?[/SIZE][/FONT]

---

### Post by adm1968 on 2009-11-01
[FONT="Georgia"][SIZE="3"]Well, found a really simple method:

    
sudo aptitude install mercurial linux-headers-$(uname -r) build-essential subversion gcc make

    
wget [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw)
    
sudo mv dvb-usb-af9015.fw /lib/firmware/
    
hg clone [http://linuxtv.org/hg/~anttip/af9015](http://linuxtv.org/hg/~anttip/af9015)
    
cd af9015

make
   
sudo make install


As easy as that!
It made everything work with Me TV
(not with Kaffeine, unfortunately)

Original method available (in Spanish) at
[http://nosinmiubuntu.blogspot.com/2009/05/avermedia-volar-x-a815-en-ubuntu-904.html]("http://nosinmiubuntu.blogspot.com/2009/05/avermedia-volar-x-a815-en-ubuntu-904.html")[/SIZE][/FONT]

---

### Post by t0p on 2009-11-02
> **adm1968 said:**
> [FONT=Georgia][SIZE=3]Well, found a really simple method:

    
sudo aptitude install mercurial linux-headers-$(uname -r) build-essential subversion gcc make

    
wget [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw")
    
sudo mv dvb-usb-af9015.fw /lib/firmware/
    
hg clone [http://linuxtv.org/hg/~anttip/af9015]("http://linuxtv.org/hg/%7Eanttip/af9015")
    
cd af9015

make
   
sudo make install


As easy as that!
It made everything work with Me TV
(not with Kaffeine, unfortunately)

Original method available (in Spanish) at
[http://nosinmiubuntu.blogspot.com/2009/05/avermedia-volar-x-a815-en-ubuntu-904.html](http://nosinmiubuntu.blogspot.com/2009/05/avermedia-volar-x-a815-en-ubuntu-904.html)[/SIZE][/FONT]

adm1968: did you translate from the Spanish?  If so: thanks!  If not: thanks for posting it here!

I'm going to buy a TV-stick sometime soon, so all input like this is very welcome.  If anyone else has anything else to add: I'm all ears!  :p

---

### Post by joshoekstra on 2009-11-10
If we are still talking about the volar X, it works out of the box with 9.04 and 9.10. Only thing you might have to do is download the latest firmware and place it in /lib/firmware, that's all there is to it...

---

### Post by caish5 on 2010-02-07
Does anyone know how to get the remote control working on this one?

---

### Post by jimmers on 2010-02-08
Hi t0p,
I run the Avermedia DVB-T Volar X, I also got it from Maplins, and it works straight out of the box in Jaunty,  using Kaffeine, but like ADM1968 I could never get it to work in Karmic, but I think I will wait until Lucid emerges, and see how it works with that Dist.
But if you change your mind this is the Stick to get.

---

