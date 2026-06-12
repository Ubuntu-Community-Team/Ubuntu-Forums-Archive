---
title: "Need help with Terratec Cinergy C PCI (DVB-C)"
date: 2008-07-12
forum: Multimedia Software
---

### Post by OttifantSir on 2008-07-12
As the title states, I have purchased this card, but I can't use it, as it isn't recognized. I have looked around the web and these forums, but noone seems to have the same card, only older ones.

According to one site dealing with ivtv, this card should be automatically recognized because of the chipset being included in the kernel since 2.6.21, but no luck.

Other information:
8.04 LTS Desktop
MSI P6NGM-FD
Intel Core2Duo E4600 2.4Ghz
2GB RAM
NEC AD7200S SATA DVD-/+RW/-RAM
WD Caviar GP 1TB
HIS Powercolor Radeon 2400 PRO 256MB

The chipset in the card (according to faulty memory) is SAA7134. (May be different arrangement of the last two digits)

Programs I have tried: VLC, gxine, MeTV, Zapping, Totem, MPlayer. All say something like: No capture card/device couldn't be opened/no DVB card recognized.

The visual output is on a Toshiba 22" TV through a DVI-HDMI cable

Please help me with this. I wanna get rid of all discs and old VHS-tapes, and not have to swith input on my TV to watch programs.

Any other info needed? Give me the command (first mediaPC ever, and anything new still makes me nervous, even after 20 years of computing) and I'll report the results. Best of all would likely be a howto, but I haven't found any.

---

### Post by xc3RnbFO8P on 2008-07-12
Did you check this site:
[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C]("http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C")
Compare the output of 
$ lspci -v -s 01:01.0
 and
$ lspci -vvn -s 01:01.0

---

### Post by OttifantSir on 2008-07-13
I get nothing from those two commands. And I mean nothing. I've tried them with/-out sudo, and I've even tried running them as root and at the root of the filesystem. Nothing. No errors, no outputs. Nothing.

Haven't tried the steps outlined in the webpage, but they seem worth the effort. Will test them later.

---

### Post by xc3RnbFO8P on 2008-07-13
Start with this:
> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
> cd v4l-dvb
> make all
> sudo make install
restart the computer
try Kaffeine.

---

### Post by OttifantSir on 2008-07-13
What exactly does the (uname -r) or `uname -r` mean? And is this the actual code to enter? I have done something a few months ago that involved this code, and it didn't seem to work then. I seem to recall having written something else there to make that action work.

Anyway, what does it mean?

---

### Post by xc3RnbFO8P on 2008-07-13
uname-r is the kernel that you use now.
Try in terminal:
> uname -r

---

### Post by OttifantSir on 2008-07-13
Well, tried the approach you outlined, and I get nothing still. VLC, gxine, MeTV, TVTime, Zapping, Kaffeine and Totem doesn't show anything. VLC doesn't complain about not finding any cards as all the others do in one way or another, but it still doesn't show me anything. It did however, output some "thumps" through my speakers this time around. It didn't before.

Tried re-running the lspci commands, and same thing as before: Nothing at all.

---

### Post by xc3RnbFO8P on 2008-07-13
Then you have to download this:
[http://jusst.de/hg/mantis/archive/08f27ef99d74.tar.bz2]("http://jusst.de/hg/mantis/archive/08f27ef99d74.tar.bz2")
Extract it to home folder, /home/your folder/ (mantis-08f27ef99d74)
> cd /home/your folder/mantis-08f27ef99d74
> make
> sudo make install

---

### Post by OttifantSir on 2008-07-13
Card recognized, but now for the final step: Do you know how to add channels to be played? I can see that Kaffeine has a built-in list of providers, but for Norway there is only Canal Digital, and I don't have that provider. I can't even begin to make heads or tails of the default channel configuration files shipped with Kaffeine. All I know is that C at the start of every line means to decode cable signal.

This is the Austrian Innsbruck file (~./kde/share/apps/kaffeine/dvb-c/at-innsbruck):

# scan config for Innsbruck Telesystem cable provider
# freq sr fec mod
C 450000000 6875000 NONE QAM64
C 490000000 6875000 NONE QAM64
C 442000000 6875000 NONE QAM64
C 546000000 6875000 NONE QAM64
C 554000000 6875000 NONE QAM64
C 562000000 6875000 NONE QAM64

I know I probably have to build my own channel file, but I need to know what these listings mean. Of course, if there is a(n) utility/application that can do it for me, I would prefer that.

Oh, thanks for helping me one step further towards a true HTPC.

---

### Post by xc3RnbFO8P on 2008-07-13
Did you try to google your provider?
If you know the frequency, you can add it to your list
> # no-Grimstad-CanalDigital (cable)
# , Symbol Rate, QAM Mode
C 410000000 6875000 NONE QAM64
C 418000000 6875000 NONE QAM64
C 426000000 6875000 NONE QAM64
C 442000000 6875000 NONE QAM64
C 450000000 6875000 NONE QAM64
C 458000000 6875000 NONE QAM64
C 466000000 6875000 NONE QAM64
C 474000000 6875000 NONE QAM64
C 482000000 6875000 NONE QAM64
C 490000000 6875000 NONE QAM64
C 498000000 6875000 NONE QAM64  


---

### Post by OttifantSir on 2008-07-13
I know the place to go to to get the frequency list of all the channels, but those frequencies doesn't look anything like the ones in the channel files. They are (example, not real) 121,73 or in channel form: 8 or S-8.

The channel list can be found at: [http://www.romm.no/kundesenter/kabel_tv.htm](http://www.romm.no/kundesenter/kabel_tv.htm)

If I knew how to convert these listings to the format needed in the channel files, I could have things up and running within the day. And MAYBE help others in the same predicament where I live, by providing a pre-compiled channel list to Kaffeine or for download at romm.no

---

### Post by xc3RnbFO8P on 2008-07-13
These are analog channels.
> Viktig Informasjon om vårt Digital TV tilbud
Via media samt informasjon fra ymse kilder gis det inntrykk av at alle fra høsten må ha dekoder til det digitale bakkenettet. Dette er feil.

De som er tilknyttet kabel TV får alle TV signalene levert via denne forbindelsen og trenger således ikke å forholde seg til det digitale bakkenettet.

Du som bor på Jessheim og er tilknyttet et av antennelagene har to alternativer.

    * Du kan gjøre som nå, motta signalene analogt.. Du vil motta grunnpakken, 19 analoge kanaler, som før. Du trenger ingen dekoder.
    * Du kan anskaffe digitaldekoder (Kr 950,-) fra Romerike Multimedia AS og dermed motta gunnpakken digitalt i tillegg til analogt, uten pristillegg. Med digitaldekoder kan du i tillegg abonnere på oppmot 60 digitale kvalitetskanaler.

Do you have this **digitaldekoder**?

---

### Post by OttifantSir on 2008-07-13
I don't see why I would need this digital decoder when I have a TV-card that reads digital signals. There isn't as if I need to have a subscription card plugged in to get the digital signals for the basic package.

Just a little thought that popped in my head: I may need to ask them to enable digital transmission for my cable. I have what else they said I needed on another page; HD-ready TV, HD-ready decoder, cable connection.

Maybe I won't be able to get this up and running today after all. They're not open on Sundays. Will call them first thing tomorrow to hear what they have to say, and post back then.

---

### Post by xc3RnbFO8P on 2008-07-13
> I don't see why I would need this digital decoder when I have a TV-card that reads digital signals.
> * Du kan anskaffe digitaldekoder (Kr 950,-) fra Romerike Multimedia AS og dermed motta gunnpakken digitalt i tillegg til analogt, uten pristillegg. Med digitaldekoder kan du i tillegg abonnere på oppmot 60 digitale kvalitetskanaler.
The signal is scrambled.

---

### Post by zaurus on 2008-07-24
Hello

I used information of this tread to install Mantis driver for my Twinhan DVB-S SP400 card. Compilation and installation worked well, driver is loaded also but does not work when I scan channels, I have initialization error on every frequency.
Is there any conflict with my other DVB-S Pinnacle PCTV-SAT card?

KR

---

### Post by rune.evjen on 2008-08-09
I have a Terratec Cinergy C PCI (lspci verifies that this card is the same as described in [http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C))

I compiled the latest mantis drivers from [http://jusst.de/hg/mantis](http://jusst.de/hg/mantis), but when I try to load the mantis module with
```
sudo modprobe mantis
```
modprobe gives the following error:
FATAL: Error inserting mantis (/lib/modules/2.6.24-20-generic/kernel/drivers/media/dvb/mantis/mantis.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and dmesg gives the following errors:
[ 7844.236138] mantis: disagrees about version of symbol dvb_dmxdev_init
[ 7844.236142] mantis: Unknown symbol dvb_dmxdev_init
[ 7844.236166] mantis: disagrees about version of symbol lnbp21_attach
[ 7844.236167] mantis: Unknown symbol lnbp21_attach
[ 7844.236333] mantis: disagrees about version of symbol dvb_register_adapter
[ 7844.236335] mantis: Unknown symbol dvb_register_adapter
[ 7844.236430] mantis: disagrees about version of symbol tda10021_attach
[ 7844.236431] mantis: Unknown symbol tda10021_attach
[ 7844.236510] mantis: disagrees about version of symbol tda10023_attach
[ 7844.236512] mantis: Unknown symbol tda10023_attach
[ 7844.236616] mantis: disagrees about version of symbol dvb_net_init
[ 7844.236618] mantis: Unknown symbol dvb_net_init
[ 7844.236666] mantis: disagrees about version of symbol dvb_dmxdev_release
[ 7844.236668] mantis: Unknown symbol dvb_dmxdev_release
[ 7844.236767] mantis: disagrees about version of symbol dvb_net_release
[ 7844.236769] mantis: Unknown symbol dvb_net_release
[ 7844.236846] mantis: disagrees about version of symbol dvb_unregister_frontend
[ 7844.236848] mantis: Unknown symbol dvb_unregister_frontend
[ 7844.236966] mantis: disagrees about version of symbol dvb_register_frontend
[ 7844.236968] mantis: Unknown symbol dvb_register_frontend
[ 7844.237004] mantis: disagrees about version of symbol stv0299_attach
[ 7844.237026] mantis: Unknown symbol stv0299_attach
```

uname -a
```
Linux server 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux

Has anyone used the mantis drivers on amd64 ?

Rune

---

### Post by rune.evjen on 2008-08-22
As a reply to the previous (my own) post,

compiling and using mantis with amd64 works fine.

The error messages I got was because I tried to unload and load modules without rebooting.

After a reboot it was fine.

---

### Post by zaurus on 2008-08-22
> **rune.evjen said:**
> As a reply to the previous (my own) post,

compiling and using mantis with amd64 works fine.

The error messages I got was because I tried to unload and load modules without rebooting.

After a reboot it was fine.

Lacky you, I still no chance with my DVB-S/S2 SP400 card from Twinhan. It refuses to work with Mantis what ever I try.
Your card is a clone of Twinhan as far as I know so it should work for me also it it works for you. What exactly driver did you use? And what scan and czap? Can you point me to the instructions you used?

KR

---

### Post by Juzz on 2010-02-09
Can anyone who has a working card with current kernel please let me know how they did?

I've tried loads of stuff and has not yet been able to make mine work - it does give the same output as the lspci found on the linuxtv wiki page...

---

