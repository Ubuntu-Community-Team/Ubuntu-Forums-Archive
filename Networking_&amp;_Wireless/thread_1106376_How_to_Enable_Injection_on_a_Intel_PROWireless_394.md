---
title: "How to Enable Injection on a Intel PRO/Wireless 3945ABG Wireless Card??"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-25
Hi

Can anybody tell(or even better) give me a tutorial on how to enable my Intel PRO/Wireless 3945ABG Wireless Card to allow packet injection??

Please be gentle I am still a relative new comer to UBUNTU..

I understand I need to update the driver for the above card, and this is where my problem lies??

How do I go about this.

What is the Terminal command to update the driver for the above wireless card, to allow injection of packets??

I look forward to your replies

---

### Post by alimahmoudy on 2009-03-25
Why do you need Packet injection ? :P 
Anyways, follow these steps carefully and you should have no trouble enabling packet injection.

Open a terminal and type the following commands


sudo apt-get install build-essential (get core files)

sudo apt-get install libssl-dev (get supporting library)

wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2) (downloads driver)

tar -xjf ipwraw-ng* (extract the archive file)

cd ipwraw-ng (go to the extracted folder)

make (compile the source files into a binary)

sudo make install (install the driver)

sudo make install_ucode

echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

sudo depmod -ae (create a dependency file for the modules)

sudo modprobe -r iwl3945 (unload driver that you do not need)

sudo modprobe ipwraw (load the driver that you installed)

sudo ifconfig wlan0 up (enable the network adapter)

When you're done, open a terminal and type lsmod, you should see the ipwraw driver loaded.

I got these steps from search results on google, you should try it sometime. good luck. hope it works.

---

### Post by scrypt on 2009-03-25
Hi

Thank-you for your quick reply...

I am able to add each command into the terminal successfully.

Up until I get to the:

wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2)

Command. which I then get the error output:

 wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2)
--2009-03-25 22:35:30--  [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2)
Resolving dl.aircrack-ng.org... 213.186.33.2
Connecting to dl.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-25 22:35:30 ERROR 404: Not Found.

I have not entere any later commands because I am a little unsure how to ut them into terminal correctly...

Can you please tell me step by step how to put each command into the terminal...

Thank's alot for your help

---

### Post by alimahmoudy on 2009-03-25
oh sorry about that dude. 

type wget http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2

---

### Post by scrypt on 2009-03-25
hi again

I tried again the commands you gave me and when i enter the command:

'tar -xjf ipwraw-ng*'

I get the error output:

mark@ubuntu:~$ tar -xjf ipwraw-ng*
tar: ipwraw-ng: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: ipwraw-ng-2.0.0-10072007.tar.bz2: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.1: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.2: Not found in archive
tar: Error exit delayed from previous errors


What does this mean???

Cheers

---

### Post by scrypt on 2009-03-25
Hey mate.

im still trying

---

### Post by alimahmoudy on 2009-03-25
never mind that, it's because you haven't downloaded the file from the link i gave you, via the wget http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2 command.
when you enter this command and download the file, just complete the other steps and all should be fine.

---

### Post by IsmailBhai on 2009-03-25
i didnt think packet injection was possible with 3945

---

### Post by scrypt on 2009-03-25
Hey again

apparantly it is possible

I used this

[http://www.maxi-pedia.com/crack+WEP](http://www.maxi-pedia.com/crack+WEP)

---

### Post by alimahmoudy on 2009-03-25
It is possible

---

### Post by scrypt on 2009-03-25
The wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)

Worked fine...

But when I use the nest command:

 sudo tar -xjf ipwraw-ng* (to extract the archived files) 

I get this output:

mark@ubuntu:~$ sudo tar -xjf ipwraw-ng* 
tar: ipwraw-ng: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: ipwraw-ng-2.0.0-10072007.tar.bz2: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.1: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.2: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.3: Not found in archive
tar: ipwraw-ng-2.3.4-04022008.tar.bz2.4: Not found in archive
tar: Error exit delayed from previous errors

Any Suggestions...

---

### Post by alimahmoudy on 2009-03-25
i'm sorry.
in the terminal, type dir
can you see a folder called ipwraw-ng ?

---

### Post by scrypt on 2009-03-25
It's all legit... 

I am learning about how strong or vulnerable WEP encryption is on one of my own WEP networks

---

### Post by scrypt on 2009-03-25
Im learning all about 'dir' and terminal commands as i am going along.

I find that i am a quick learner, so I am using this exercise as a learning curve not only about Wep encryption but also Terminal commands and directories...

I appreciate your help.

I see that dir needs to be entered.

Can you be a bit more specific.

ie can you show me the correct terminal entries step by step.

I will use tis as future terminal command execution references.:)

---

### Post by scrypt on 2009-03-25
Yes i can see the ipwraw-ng folder

It is on my desktop

---

### Post by alimahmoudy on 2009-03-25
Well when you received that error, it said that ipwraw-ng is a directory. It means you have already extracted the downloaded files.
So you need to type dir in the terminal, that way you can see the folders and files in your home directory.
Then you continue with the steps, by typing cd ipwraw-ng you enter the specified directory. and then you go on...

---

### Post by alimahmoudy on 2009-03-25
if the folder is on your desktop, then you need to type: cd Desktop/ipwraw-ng ( don't forget the capital D in Desktop )
and then continue :)

---

### Post by scrypt on 2009-03-25
Okay..

I am now at:

mark@ubuntu:~/Desktop/ipwraw-ng$ 

I am in the correct directory.

---

### Post by alimahmoudy on 2009-03-25
Good to know that. You can go on with the other steps now. Everything should work smoothly.

---

### Post by scrypt on 2009-03-25
So if i am correct the next command is:

mark@ubuntu:~/Desktop/ipwraw-ng$ sudo make

Is this correct.

I get the jist about directories now.

Thank's for that

---

### Post by alimahmoudy on 2009-03-25
Yep

---

### Post by scrypt on 2009-03-25
Okay i used the:

mark@ubuntu:~/Desktop/ipwraw-ng$ sudo make  'command'

it gave me this?

am i still on the right path??

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.27-14-generic/build M=/home/mark/Desktop/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-14-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/mark/Desktop/ipwraw-ng/ipwraw.o
  Building modules, stage 2.

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  MODPOST 1 modules
  CC      /home/mark/Desktop/ipwraw-ng/ipwraw.mod.o
  LD [M]  /home/mark/Desktop/ipwraw-ng/ipwraw.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
make[1]: Entering directory `/home/mark/Desktop/ipwraw-ng/util'
gcc -I/lib/modules/2.6.27-14-generic/build/include -Wall -c -o wifi_tx.o wifi_tx.c
gcc -Wall -o wifi_tx wifi_tx.o
make[1]: Leaving directory `/home/mark/Desktop/ipwraw-ng/util'
mark@ubuntu:~/Desktop/ipwraw-ng$

---

### Post by alimahmoudy on 2009-03-25
Yeah you are.

---

### Post by scrypt on 2009-03-25
When irun the 'sudo modprobe -r iwl3945' command My whole system freezes and my caps lock button light flashes continuously every 1 second.

Why is this? do you have any idea??

---

### Post by alimahmoudy on 2009-03-25
hmm.
It's because your're currently using the wirless card. so the drivers are currently being used.
try disconnecting and turning off your wireless card, or type sudo ifconfig wlan0 down before typing the modprobe command.

---

### Post by scrypt on 2009-03-25
Hi again mate.

I ran the three last commands to finish off

closed the terminal and then ran the 'lsmod'

and this is what it gave me.

Has it worked correctly can yuo see the correct driver installed.

I am grateful to have an expert helping me out??

mark@ubuntu:~$ lsmod
Module                  Size  Used by
ipwraw                125848  0 
ipv6                  264228  10 
af_packet              25856  4 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44304  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12680  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
snd_hda_intel         385072  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
arc4                    9984  2 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                99316  0 
rfkill                 17048  2 iwl3945
mac80211              216820  1 iwl3945
evdev                  17696  11 
sdhci_pci              15360  0 
led_class              12164  1 iwl3945
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                18436  0 
container              11520  0 
psmouse                45200  0 
tifm_7xx1              13824  0 
sdhci                  23940  1 sdhci_pci
video                  25488  0 
output                 11008  1 video
yenta_socket           31756  1 
serio_raw              13444  0 
tifm_core              16028  1 tifm_7xx1
mmc_core               58268  1 sdhci
cfg80211               32392  2 iwl3945,mac80211
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore              15328  1 snd
pcspkr                 10624  0 
intel_agp              33980  0 
agpgart                42184  2 drm,intel_agp
ac                     12292  0 
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133384  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
loop                   23052  2 
sd_mod                 42392  2 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_piix               24708  1 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                177824  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
e100                   41356  0 
mii                    13440  1 e100
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
uhci_hcd               30736  0 
ehci_hcd               43788  0 
usbcore               149488  3 uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42284  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  5

---

### Post by scrypt on 2009-03-25
If I am not mistaken it has all gone according to plan...

I can see:

 ipwraw 125848 0 

On the third line down, of the lsmod command

---

### Post by scrypt on 2009-03-25
Im pretty sure the reason my sytem was freezing when i ran the:


'sudo modprobe -r iwl3945' command

Was becuase I was trying to unload the wireless driver that is in use at the time.

So this is why it was freezing:P

---

### Post by alimahmoudy on 2009-03-25
Lol, scroll up, i told you how to prevent the system from freezing, you're right, that's the reason. 
Well you seem the have skipped the modprobe -r step.
you can't skip it, as it is used to remove the original drivers
as you can see, you have installed the ipwraw drivers, but the old ones iwl3945 and
mac80211 are still there, you need to remove them.

---

### Post by scrypt on 2009-03-25
Ha Ha..

Sorry missed that post in my haste..

I read that in some cases I will lose internet connection on my wireless card ehrn i implement the desired driver for the packet injection?

Do you know if this is true?

and if so how do I employ internet connection back to the wireless card??

Also How can I check to see if the earlier commands where fully successful in adding packet injection to my Wireless card??

---

### Post by alimahmoudy on 2009-03-25
Did it work ? did you remove the old drivers ?
You will lose internet connection when you set your wireless card to monitor mode. Usind the command sudo iwconfig wlan0 mode monitor.
you can set it back, by typing sudo iwconfig wlan0 mode managed.
And you're using aircrack right ? 
Type sudo airodump-ng wlan0 and see what it says ( You need to put the card in monitor mode first )

---

### Post by scrypt on 2009-03-25
LOL

Yep to answer mine and your question it did indeed lose internet connection.

I have sparked up mg from y other laptop so i am posting from it because it has internet connection...

I succesfully removed the not needed first drivers..

How do i check if it wasall successfull

---

### Post by alimahmoudy on 2009-03-25
post the output of the command lsmod | grep 3945
What program are u using to "test your network" ?
aircrack ? if so, scroll up and use the command i wrote.

---

### Post by scrypt on 2009-03-25
Ha Ha.

One problem

I cannot post the outut from the laptop that we just updated the driver for the Intel Wireless card because it no longer has internet access. lol.

I am using Aircrack Yes...

Is there a quick way to Change the connection settings on the other Laptop (The One we just updated the driver on)

So that I can post the Output from the coomands you just gave me.

---

### Post by alimahmoudy on 2009-03-25
dude...scroll up and read lol !

---

### Post by scrypt on 2009-03-25
Right okay..

Im posting my next questions before I get your last answers...

Soz about that. seems to be a bit of a delay..

Im having trouble with the:

 'sudo iwconfig wlan0 mode monitor' and the
 'sudu iwconfig wlan0 mode managed'

I get:

error  for wireless request "set mode" (8B06) : SET failed on device wlan0 ; No such device.

I have plugged the laptop with the wireless card by ethrnrt LAN connection. So i can post the terminal output from th laptop we are working on (Relief)

---

### Post by alimahmoudy on 2009-03-25
type iwconfig and post the output

---

### Post by scrypt on 2009-03-25
Here is the sudo iwconfig output:

mark@ubuntu:~$ sudo iwconfig
[sudo] password for mark: 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by alimahmoudy on 2009-03-25
ok, type sudo ifconfig eth0 up
and then try sudo iwconfig eth0 mode monitor or managed and see if it works

---

### Post by scrypt on 2009-03-25
Okay.

Before i type the last command you gave me, the:

'sudo ifconfig eth0 up'  command

I rebooted. and manged to coonect wirelessly to the net.

Right. here is the sudo 'iwconfig output' now.

This is before i have used the command 'sudo ifconfig eth0 up'

Which I hve not used yet...

---

### Post by scrypt on 2009-03-25
sudo iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"ROUTER"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:74:6C:22:96   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:2387-BFEE-4C96-8850-5522-9F08-8314-43B8-3BD9-D7A9-1E56-0F13-0ACF-1D8B-4869-2D6C [2]   Security mode:open
          Power Management:off
          Link Quality=98/100  Signal level:-26 dBm  Noise level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by alimahmoudy on 2009-03-25
okay. so the commands should work now, since you have the device wlan0 present :)

---

### Post by scrypt on 2009-03-25
Here is the output from 'sudo lsmod | grep 3945' command:

mark@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@ubuntu:~$ sudo lsmod | grep 3945
iwl3945                99316  0 
rfkill                 17048  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211

---

### Post by scrypt on 2009-03-25
Patience is so definately a virtue

---

### Post by scrypt on 2009-03-25
Right... Okay..

I ran the  'sudo iwconfig wlan0 mode monitor' and got this output:

mark@ubuntu:~$ sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

---

### Post by alimahmoudy on 2009-03-25
haha ! definitely !
You STILL have the iwl3945 drivers loaded, as you can see.

did you execute the command modprove -r iwl3945 correctly ??

---

### Post by scrypt on 2009-03-25
okay ran the 'command modprove -r iwl3945' command.
after turning OFF my wireless card.

seems to have worked.

Not internet wireless internet connection.

Im back connected by LAN Ethernet...

Whats the next step??

and thanks for sticking it out with me I've learned such a lot in the last hour

---

### Post by alimahmoudy on 2009-03-25
Well let me explain a little bit.
you use the command modprobe -r iwl3945 to remove the old driver.
and the command lsmod | grep 3945 to check if it has been removed.
then type lsmod | grep ipwraw to see if the ipwraw driver is loaded.

Did you execute these commands step by step ?

echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

sudo depmod -ae (create a dependency file for the modules)

sudo modprobe -r iwl3945 (unload driver that you do not need)

sudo modprobe ipwraw (load the driver that you installed)

sudo ifconfig wlan0 up (enable the network adapter)

If you did, then you should have no problem. just type iwconfig in order to display your devices. 
If wlan0 is present, then use sudo iwconfig wlan0 mode monitor, and start using airodump-ng and aircrack-ng to crack the WEP key.

---

### Post by scrypt on 2009-03-25
sudo iwconfig:

 sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

npe looks like i have not.

Right time to backtrack a little.

Thanks agian for the clear concise advice

---

### Post by scrypt on 2009-03-25
Did you execute these commands step by step ?

echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

can I start with the command: 'sudo depmod -ae' in a new terminal?

will that be fine to do??

sudo depmod -ae (create a dependency file for the modules)

sudo modprobe -r iwl3945 (unload driver that you do not need)

sudo modprobe ipwraw (load the driver that you installed)

sudo ifconfig wlan0 up (enable the network adapter)

---

### Post by alimahmoudy on 2009-03-25
yes you can

---

### Post by scrypt on 2009-03-25
I ran the last couple of commands and all seemed to be fine until i use the:

'sudo ifconfig wlan0 up' command and it give me this output:

 sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

I then ran 'sudo iwconfig'
and it gave me this output:

 sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

---

### Post by alimahmoudy on 2009-03-25
ok, so wifi0 is your device.
and it's already set to monitor mode as you can see.

to use internet connection, now you type sudo iwconfig wifi0 mode managed

try using the airodump-ng and aircrack-ng commands now, see if they work. Remember, your wifi0 must be set to monitor mode before you use them.

---

### Post by scrypt on 2009-03-25
You are a star...

I can see this being used a a tutorial for begginers for years to come LOL

---

### Post by scrypt on 2009-03-25
Right do you fancy teaching your new cyber friend the basics of Aircrack??

Have you ever heard the saying:

It's not what you know it's who you know...

I like that phrase and i use it.

And it's never rang more true than now.

I thank-you  alimahmoudy

---

### Post by alimahmoudy on 2009-03-25
Lol ! well it's ali and my family name is mahmoudy actually.
anw, go to [http://www.aircrack-ng.org/doku.php?id=tutorial](http://www.aircrack-ng.org/doku.php?id=tutorial)
you'll find everything you need there. This forum is for Ubuntu remember :P ?
Glad to help you out dude. You're welcome.

---

### Post by scrypt on 2009-03-25
Okay i'll check the link out..

Will it be okay if I drop you a message every now and agin to pick your brains. Ha Ha.

---

### Post by alimahmoudy on 2009-03-25
Are you a sexy girl ? If you are then anytime ! 
if you're not, well...Haha

---

### Post by scrypt on 2009-03-25
Ha Ha.. 

I won't close this post as solved just yet..

But by the way It's all working like a charm...

---

### Post by alimahmoudy on 2009-03-25
> **scrypt said:**
> Ha Ha.. 

Trust me bro im only interested in your cyber advice LOL.

I won't close this post as solved just yet..

But by the way It's all working like a charm...

Lol, i was kidding man.
you're welcome anytime. take care.

---

### Post by scrypt on 2009-03-25
Hey mate.

Im having alitle trouble agin.

It was running fine untill a while ago and know i canot seem to get it into monitor mode agin.

I reviewed the erlier posts but ive had no luck rectifying it.

I know it works if set correctly.

But im not sure where im going wrong...

Here is the sudo iwconfig output:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

can you give me a bit more input?

---

### Post by scrypt on 2009-03-25
I think it might have something to do with when I reboot my system. I reckon the old driver still reloads, Because I can connect to the net wirelessly as soon as i start my system?

I have an the 'sudo echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw' command, as you said, but i think this may be the culperate??

Can you help??

---

### Post by scrypt on 2009-03-25
Im still having a little trouble with the original driver loading at startup (well at least i think that is what it is)

I have ran the echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw command

But ithink the original driver might still be loading at startup?

can yo help?

---

### Post by scrypt on 2009-03-26
No worries I have suused it after applying the correct commands.

I need to reboot ubuntu for the Desired efects to take place.

I know mate i suppose it's my slightly sarcy english wit.

some people take it the wrong way sometimes.

Thank's again for the help

Much appreciated.

I've been pluging away for a good day of so to get this driver patch applied successfuly...


scrypt

---

### Post by scrypt on 2009-03-26
Im not sure if the original ipfwaw Default driver is being blacklisted correctly??

Does this command need to be entered into the terminal as it is show (In one line)

  | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

Or does it need to be entered into two sepwrate commands?
eg:
 echo "blacklist ipwraw"

and:
   sudo tee /etc/modprobe.d/ipwraw ???

I think this is where my problems are?

I think the original default ipwraw is not being blacklisted correctly

Can anyone help??

---

### Post by scrypt on 2009-03-26
Hey mahmoudy...

I had on quick succesfull session after your commands you gave me.

But after rebboting I connected wirelessly to the Net when my card should have been in monitor mode.

I can NO longer run my card correctly, and I am really not sure where I have gone wrong??

I have followed your earlier instuctions to the letter. But I am no longer able to get the same output and desired Card behaviour?

Anychance you can help me rectify this and maybe find out where I am going wrong??

To begin with I think the Original wireless driver is still loading at bootup, along either the new driver, So somehow it is not geting blacklisted correctly??

Cheers for now...

---

### Post by scrypt on 2009-03-26
Im still having the same issues. I have followed the earlier comands to the letter, which worked fine earlier.

But I cannot run them properly this time around

Can anyone help

---

### Post by scrypt on 2009-03-26
I want to correctly patch my intel pro/wireless 3945abg with this driver:

        wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2)            (downloads driver)

 What are the correct commands to apply the above driver? 

 and also what is the correct command to Blacklist the original default Wireless card driver??
Because this is where I think my problem lies, That it is not coorectly blacklistung and removing the original default driver?

   I have tried this this bellow command I was given to blacklist it, but it still reloads when I re-boot Ubuntu 8.10:

   sudo modprobe -r iwl3945          (unload driver that you do not need).

I then use this command to load the new Driver:

                sudo modprobe ipwraw                 (load the driver that you installed)

 Then I use this command to restart my wireless card along with actually turning on the power suppt too it:

               sudo ifconfig wlan0 up (enable the network adapter): This command never workd though, I get this output form the iwconfig command:

I can put my card into monitor mode using this command:   
                                                                                                   sudo iwconfig wlan0 mode monitor


This seems to work and does put my card into monitor mode. BUT does not change it fully because it should change from wlan0 to wifi0, which it doea not!

Can anyone see where i am going wrong?

also can anybody advise me how to rectify this??

---

### Post by scrypt on 2009-03-26
Hi

Afer more research into my problem I am pretty sure it is because the original default driver is not being blacklisted correctly.

Can someone show me how to Do it correctly??

---

### Post by scrypt on 2009-03-28
Hey ali.

I can get my card into monitor mode even after a reboot (Sorted)

BUT I cannot set it back to managed mode? using the command you gave me?


mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

pan0      no wireless extensions.

I also cannot find the network using the:

sudo airodump-ng

---

### Post by scrypt on 2009-03-28
Hey Ali Mahmoudy

I have got my card patched and working in monitor mode.

BUT I am not able to inject packets from it??

It can be done because I done it briefly the other day you helped me out?

I am not sure what has chwnged in the mean time?

any ideas??

---

### Post by scrypt on 2009-03-28
My whole system was freezing each time i ran:

 sudo airodump-ng wifi0

untill i used this command that you gave me:

sudo depmod -ae (create a dependency file for the modules)

---

### Post by scrypt on 2009-03-29
I Could really do with some assistance Ali???

---

### Post by alimahmoudy on 2009-03-30
Sorry i haven't been online for a few days..been busy with shootings.
anyways, when did the problem occur ? suddenly or after you restarted your system ? 
post the output of the commands ```
iwconfig
``` and [HTML][/HTML]```
lsmod
```

---

### Post by scrypt on 2009-03-31
Hey Mate...

No problem. Cheers for getting back to me

Here are the terminal output for the two commands (iwconfig) + (lsmod)

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

pan0      no wireless extensions.



mark@ubuntu:~$ lsmod
Module                  Size  Used by
af_packet              25856  2 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
sco                    18308  2 
rfcomm                 44304  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
vboxdrv                71576  0 
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
wmi                    14504  0 
ipt_REJECT             11136  0 
ipt_LOG                13700  0 
xt_limit               10372  0 
ipt_addrtype           10496  0 
xt_state               10112  0 
xt_tcpudp              11008  0 
xt_conntrack           11904  0 
ip6table_filter        10624  1 
ip6_tables             21008  1 ip6table_filter
ipv6                  264228  10 
nf_nat_irc             10240  0 
nf_conntrack_irc       13348  1 nf_nat_irc
nf_nat_ftp             10880  0 
nf_conntrack_ftp       15652  1 nf_nat_ftp
ipwraw                125848  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
tifm_sd                18184  0 
pcmcia                 43052  0 
snd_hda_intel         385072  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
sdhci_pci              15360  0 
iTCO_wdt               18596  0 
serio_raw              13444  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
sdhci                  23940  1 sdhci_pci
evdev                  17696  11 
pcspkr                 10624  0 
tifm_7xx1              13824  0 
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                45200  0 
tifm_core              16028  2 tifm_sd,tifm_7xx1
yenta_socket           31756  1 
mmc_core               58268  2 tifm_sd,sdhci
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
fglrx                1813832  30 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
container              11520  0 
video                  25488  0 
output                 11008  1 video
soundcore              15328  1 snd
ac                     12292  0 
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
battery                18436  0 
shpchp                 38036  0 
intel_agp              33980  0 
agpgart                42184  2 fglrx,intel_agp
pci_hotplug            34976  1 shpchp
iptable_nat            13448  0 
nf_nat                 25368  3 nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      21900  3 iptable_nat,nf_nat
nf_conntrack           72032  9 xt_state,xt_conntrack,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  0 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  10 ipt_REJECT,ipt_LOG,xt_limit,ipt_addrtype,xt_state,xt_tcpudp,xt_conntrack,ip6_tables,iptable_nat,ip_tables
ext3                  133384  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
loop                   23052  4 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ata_piix               24708  1 
e100                   41356  0 
mii                    13440  1 e100
ohci1394               37936  0 
libata                177824  3 pata_acpi,ata_generic,ata_piix
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149488  3 ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42284  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  5

Your just the man to aks this!

How can I Discover/Find hidden wirless AP's ie ones that do not broadcast there SSID?

I have had a good google, but I have not been able to find any concise instuctions for doing so using Ubuntu??

---

### Post by alimahmoudy on 2009-03-31
Well as you can see, the ipwraw drivers is loaded correctly, and the intel driver isn't. 
And as for your wireless device, it's wifi0 and it's in monitor mode.
How do you know it's not injecting packets ? everything seems fine to me to start injecting packages. 
Also when you type ```
sudo airodump-ng wifi0
``` what happens ?

---

### Post by scrypt on 2009-04-01
Hey mate.

It is injecting packets fine know. Thanks

The only problem I am having is when I run the commands to put my card back into Managed mode for surfing the net.

I had a little trouble with the ones you gave me.

I got these commands from Chili555 (Thanks Chili).

He showed me how to put my card into managed mode, up until I reboot.  Then my card automaticaly goes back into monitor mode.

They worked fine.. 

BUT. I have decided to not broadcast my SSID.
So know I cannot surf the net wirelessly by using chili's commands.
which did work fine up until I hid my SSID.

These are the commands Chili gave me to put my card back into managed mode and visa versa:

To put my card bck into Managed (Surfing Mode) use these:

sudo rmmod -f ipwraw
sudo modprobe iwl3945
sudo ifup wlan0 mode managed rate 54M

When you reboot, because of the settings we set up, it will revert to ipwraw in 'monitor mode.
__________________

To go back to monitor mode is simply the reverse:
Code: Or Re-Boot. to auto matically get monitor wifi0 mode

sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe ipwraw

Do you have any idea how I can rectify this??

---

### Post by alimahmoudy on 2009-04-01
hmm, sorry mate, i have no idea. good luck anyways :)

---

### Post by mayuroks on 2009-04-03
hey !!! the method dat u gave was for UBUNTU. can u suggest something for VISTA too ...i mean how to enable it in with only VISTA,,,,,no SP1

---

### Post by alimahmoudy on 2009-04-03
well i don't know about that man. try google. i have no idea on how to do it on vista.

---

### Post by scrypt on 2009-04-03
Hey Ali..

I have got package injection running perfectly.
and also managed to find my WEP key  :)

Im trying it with WPA-PSK now

im getting there but I need to know how to add a wordlist/dictionary for the brute-force attack.

can you tell me ow to add a wordlist/dictionary to my command :

It would be something like this : 

 sudo aircrack-ng -w password.lst -b 00:00:00:00:00:00 psk*.cap

any suggestions??

---

### Post by scrypt on 2009-06-18
[html]code[/html]

---

### Post by alimahmoudy on 2009-06-18
hey, a little bit late huh ?
the command should be used with -r instead of -w
u could use the command:
aircrack-ng --help
for furthe instructions.

---

### Post by NoOne121 on 2009-06-18
Just in case anyone reads this and thinks that they have to jump through hoops to get packet injection running with 3945ABG on ubuntu.
It works by default in Jaunty, ubuntu 9.04. Nothing needed to be installed except of course aircrack-ng.

forgot to mention use the iwl3945 driver....the mac80211 version....not the ipwraw one mentioned here as its outdated now.

---

### Post by scrypt on 2009-06-18
Hey Ali...

How's tricks??

All is works well with my intel wlan card and it allows injection.


I have A BCM4312 Wlan card in my other main laptop and I'm trying to get injection working on it.

I have read loads about it, but Ive also read that NO it won't allow injection and then I also read others say it can allow injection.

Do you reckon you can help to see if we can get it working (Allow injection)

as for this thread about my Intel Pro/Wirelss 3945ABG.
I can add this thread SOLVED.

Thank's again for the help...

---

### Post by scrypt on 2009-06-18
Good tip NoOne121, 

it's good that things have progressed well...

---

### Post by scrypt on 2009-06-18
[html]This was solved by alimahmoudy[/html]

---

### Post by alimahmoudy on 2009-06-18
well, i got lazy and stopped looking for patches and drivers in order to enable injection.
I suggest you use backtrack or wifiway.
Both work great with my card, which is an atheros one.
Wifiway is in spanish, but it's not a big problem.
I personally use backtrack.
Both can be downloaded, burnt an run as live CDs.
*I use a USB instead of a CD*
[www.remote-exploit.org/backtrack_download.html](www.remote-exploit.org/backtrack_download.html)
and you can download wifiway via your torrent client.

---

### Post by scrypt on 2009-06-18
I've not long got backtrack 4-beta.

and i'll check your other suggestions out!!

Is there anything els I need to do to add this as solved??

---

### Post by alimahmoudy on 2009-06-18
nope, you've enabled injection successfuly right ;) ?
take care.

---

### Post by scrypt on 2009-06-18
I've been using backtrack but I can't seem to do anything else art from get internet access with my BCM4312 wlan card.

It doesn't even get recognised when I use ```
iwconfig
```

you got any suggestions??

---

### Post by alimahmoudy on 2009-06-18
try Wifiway

---

### Post by scrypt on 2009-07-10
Hey Ali.

Im running aircrack and all seems to be running okay.

BUT when I run the final command against the found IV's aurcrack says it has found the key and decrypted correctly but only shows me as Like A MAC Address instead of the ASCII.

Can you shed any light on this??

---

### Post by alimahmoudy on 2009-07-12
Hey, how's it going ?
It's all numbers right ? 
the key is the numbers you see but without the ":" of course.

---

### Post by onenegative on 2009-07-14
Hi, I am new to Ubuntu. Just installed 9.04 yesterday.

All of these commands will put me too death. lol

So anyways on page 1 you gave us a little tutorial on how to enable injection on 3945abg. I got stuck here:

> **alimahmoudy said:**
> 

sudo apt-get install build-essential (get core files)

sudo apt-get install libssl-dev (get supporting library)



When I put this command in the terminal:
sudo apt-get install libssl-dev

I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8a-7ubuntu0.9) but 0.9.8g-15ubuntu3.2 is to be installed
              Depends: zlib1g-dev but it is not going to be installed
E: Broken packages
```
What's wrong?

Please helpp me. ;)

---

### Post by onenegative on 2009-07-14
Ok, I seem to have moved on. Took me a hell of a long time to find that file but it will be wortth it when this is completed.


aman@aman-laptop:~/Desktop/ipwraw-ng$ make

Now I have another problem:
```
aman@aman-laptop:~/Desktop/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.28-11-generic/build M=/home/aman/Desktop/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/aman/Desktop/ipwraw-ng/ipwraw.o
  Building modules, stage 2.

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  MODPOST 1 modules
  CC      /home/aman/Desktop/ipwraw-ng/ipwraw.mod.o
  LD [M]  /home/aman/Desktop/ipwraw-ng/ipwraw.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Entering directory `/home/aman/Desktop/ipwraw-ng/util'
gcc -I/lib/modules/2.6.28-11-generic/build/include -Wall -c -o wifi_tx.o wifi_tx.c
gcc -Wall -o wifi_tx wifi_tx.o
make[1]: Leaving directory `/home/aman/Desktop/ipwraw-ng/util'
aman@aman-laptop:~/Desktop/ipwraw-ng$ sudo make install

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

Installing to /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ ... done

*** WARNING: Couldn't find /lib/firmware/iwlwifi-3945.ucode! ***
Don't forget to copy firmware to your hotplug's firmware directory
and have the hotplug tools in place.

You can install the firmware using
        make install_ucode

Please see the README.ipwraw for more information.

You can load the module with
        modprobe ipwraw
aman@aman-laptop:~/Desktop/ipwraw-ng$ make install_ucode

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

Installing ucode in /lib/firmware ... cp: cannot create regular file `/lib/firmware/iwlwifi-3945.ucode': Permission denied
done
aman@aman-laptop:~/Desktop/ipwraw-ng$
```:p

Problem:
Couldn't find /lib/firmware/iwlwifi-3945.ucode! ***
Don't forget to copy firmware to your hotplug's firmware directory
and have the hotplug tools in place.

When I enter:
make install_ucode

I get:
WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

Installing ucode in /lib/firmware ... cp: cannot create regular file `/lib/firmware/iwlwifi-3945.ucode': Permission denied
done

---

### Post by onenegative on 2009-07-15
Stuck at last step:

```
aman@aman-laptop:~/Desktop/ipwraw-ng$ sudo modprobe ipwraw
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
aman@aman-laptop:~/Desktop/ipwraw-ng$ 
```

What is this? Sorry for sounding Newbish. ;)

---

### Post by CyberNeT85 on 2009-08-14
Ok, im having a problem with this whole thing. Im a sorter newb. not a complete loss but im new.

heres what im doing...

sudo apt-get install build-essential
sudo apt-get install libssl-dev
wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)
tar -xjf ipwraw-ng*
cd ipwraw-ng
make
sudo make install
sudo make install_ucode
sudo depmod -ae
sudo modprobe -r iwl3945
sudo modprobe ipwraw
sudo ifconfig wifi0 up
airmon-ng start wifi0

when i do this it works fine... but. the pwr (power) is equal to 0 on all SSID's and i dont know why? and also the data doesnt increase at all. and i know it shud cus im using the ssid on another laptop.

help please.......

---

### Post by athyanop on 2009-08-21
** YOU DONT NEED TO DO ANYTHING !!** Ubuntu 9.04 comes with this driver installed !  
So this thread helps users with older version of Ubuntu. 

Also , can someone post the rollback procedure to get the un-patched driver back ?






> **onenegative said:**
> Hi, I am new to Ubuntu. Just installed 9.04 yesterday.

All of these commands will put me too death. lol

So anyways on page 1 you gave us a little tutorial on how to enable injection on 3945abg. I got stuck here:



When I put this command in the terminal:
sudo apt-get install libssl-dev

I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8a-7ubuntu0.9) but 0.9.8g-15ubuntu3.2 is to be installed
              Depends: zlib1g-dev but it is not going to be installed
E: Broken packages
```
What's wrong?

Please helpp me. ;)

---

### Post by tuxianer on 2009-11-16
Hi,
I have an Intel 3945abg card and using 9.10. Why can I enable monitor mode?

---

### Post by tuxianer on 2009-11-17
with 
[FONT=monospace]iwconfig wifi0 mode monitor I get an error.[/FONT]

---

### Post by chili555 on 2009-11-17
> iwconfig wifi0 mode monitorPlease try:```
[COLOR="Red"]sudo[/COLOR] iwconfig [COLOR="Red"]wlan0[/COLOR] mode monitor
```

---

### Post by tuxianer on 2009-11-17
yes I have tried this but I get:
```
error for the wireless request "Set Mode" (8B06)
Set failed on device wlan0; Device or resource busy
```

---

### Post by chili555 on 2009-11-17
Let's try another way:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Did that do it?

---

### Post by tuxianer on 2009-11-17
Ok thx this works for me. Is it now possible to log my wlan traffic with wireshark in plain text, when its unencrypted?

---

### Post by SirKonstantine on 2009-11-21
I just installed Compat-Wireless. I uploaded the Compat-Wireless module.

> root@MARS:/home/konstantine/Downloads/compat-wireless-2009-11-21# lsmod | grep iwl
iwl3945                70332  0 
iwlcore               119172  1 iwl3945
mac80211              212556  2 iwl3945,iwlcore
cfg80211              132808  3 iwl3945,iwlcore,mac80211


but I still can not get injection working. advice?

> root@MARS:/home/konstantine/Downloads/compat-wireless-2009-11-21# aireplay-ng -9 wlan0
14:18:59  Trying broadcast probe requests...
14:19:01  No Answer...
14:19:01  Found 1 AP 

14:19:01  Trying directed probe requests...
14:19:01  00:21:1E:3C:0B:10 - channel: 1 - 'Cornerstone'
14:19:07   0/30:   0%


---

### Post by zach_kirov on 2010-01-05
Hi I followed the instruction in [http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG](http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG)
When I do until the "make" step, I get an error like this. I have tried to use 'make SHELL=/bin/bash' and I got the same error too. May I know what is the problem please? 

-------------------------------------------------------------------------------------------
ubuntugod@ubuntu:~/ipwraw-ng$ sudo make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.31-16-generic/build M=/home/ubuntugod/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/ubuntugod/ipwraw-ng/ipwraw.o
/home/ubuntugod/ipwraw-ng/ipwraw.c:43:27: error: net/ieee80211.h: No such file or directory
In file included from /home/ubuntugod/ipwraw-ng/ipwraw.h:51,
                 from /home/ubuntugod/ipwraw-ng/ipwraw.c:48:
/home/ubuntugod/ipwraw-ng/iwlwifi_hw.h:525: error: array type has incomplete element type
/home/ubuntugod/ipwraw-ng/iwlwifi_hw.h:847: error: array type has incomplete element type
In file included from /home/ubuntugod/ipwraw-ng/ipwraw.c:48:
/home/ubuntugod/ipwraw-ng/ipwraw.h:531: error: field ‘frame’ has incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.h:532: error: ‘IEEE80211_FRAME_LEN’ undeclared here (not in a function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘frame_get_hdrlen’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: ‘IEEE80211_3ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: (Each undeclared identifier is reported only once
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: for each function it appears in.)
/home/ubuntugod/ipwraw-ng/ipwraw.c:53: error: implicit declaration of function ‘WLAN_FC_GET_STYPE’
/home/ubuntugod/ipwraw-ng/ipwraw.c:55: error: implicit declaration of function ‘WLAN_FC_GET_TYPE’
/home/ubuntugod/ipwraw-ng/ipwraw.c:56: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_FROMDS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_TODS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:58: error: ‘IEEE80211_4ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:59: error: ‘IEEE80211_STYPE_QOS_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:62: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:64: error: ‘IEEE80211_STYPE_CTS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:65: error: ‘IEEE80211_STYPE_ACK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:66: error: ‘IEEE80211_1ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:69: error: ‘IEEE80211_2ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_channel_a_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1709: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_channel_bg_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1714: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘store_channel’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1878: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:1884: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘store_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1926: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:1927: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_get_channel_info’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:3284: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:3294: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘reg_get_chnl_grp_index’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:3489: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_init_channel_map’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:4111: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4112: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_post_alive_work’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:4248: error: ‘IEEE80211_OFDM_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4249: error: ‘IEEE80211_OFDM_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4250: error: ‘IEEE80211_CCK_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4251: error: ‘IEEE80211_CCK_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_queue_tx_free_tfd’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:5974: error: implicit declaration of function ‘ieee80211_get_hdrlen’
/home/ubuntugod/ipwraw-ng/ipwraw.c:5974: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘raw_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6396: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6406: error: ‘ETH_P_80211_RAW’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6416: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c:6416: warning: its scope is only this definition or declaration, which is probably not what you want
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_data_packet’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6441: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6456: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_duplicate_packet’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6458: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6459: error: implicit declaration of function ‘WLAN_GET_SEQ_SEQ’
/home/ubuntugod/ipwraw-ng/ipwraw.c:6460: error: implicit declaration of function ‘WLAN_GET_SEQ_FRAG’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_tx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6509: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6509: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6514: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6514: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6522: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6526: error: ‘IEEE80211_RADIOTAP_HDRLEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6540: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6563: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6623: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6623: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6628: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6628: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6646: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_reply_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: error: variable ‘stats’ has initializer but incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: error: unknown field ‘rssi’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: error: unknown field ‘signal’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: error: unknown field ‘noise’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: error: unknown field ‘mac_time’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: error: unknown field ‘rate’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: error: unknown field ‘received_channel’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: error: unknown field ‘len’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6860: error: unknown field ‘freq’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: error: unknown field ‘tsf’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: error: unknown field ‘beacon_time’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: error: storage size of ‘stats’ isn’t known
/home/ubuntugod/ipwraw-ng/ipwraw.c:6881: error: ‘IEEE80211_STATMASK_RSSI’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6885: error: ‘IEEE80211_STATMASK_SIGNAL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6887: error: ‘IEEE80211_STATMASK_NOISE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6889: error: ‘IEEE80211_STATMASK_RATE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: warning: unused variable ‘stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7256: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_rate’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7263: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7264: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7295: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7302: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7303: error: ‘IEEE80211_STYPE_AUTH’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7304: error: ‘IEEE80211_STYPE_DEAUTH’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7305: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7306: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7333: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_basic’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7340: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7340: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7341: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7345: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7354: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7354: error: ‘IEEE80211_FCTL_MOREFRAGS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7359: error: ‘IEEE80211_FCS_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7366: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7366: error: ‘IEEE80211_FCTL_PROTECTED’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7382: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7383: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7384: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7385: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7386: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘tx_skb’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7420: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7422: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7423: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7430: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7439: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7491: warning: passing argument 3 of ‘ipw_build_tx_cmd_basic’ from incompatible pointer type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7330: note: expected ‘struct ieee80211_hdr_4addr *’ but argument is of type ‘struct ieee80211_hdr_4addr *’
/home/ubuntugod/ipwraw-ng/ipwraw.c:7493: warning: passing argument 3 of ‘ipw_build_tx_cmd_rate’ from incompatible pointer type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7253: note: expected ‘struct ieee80211_hdr_4addr *’ but argument is of type ‘struct ieee80211_hdr_4addr *’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_net_hard_start_xmit’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7562: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_hdr_1addr’ 
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7582: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7583: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7586: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_prom_alloc’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8374: error: ‘ARPHRD_IEEE80211_RADIOTAP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8375: error: ‘struct net_device’ has no member named ‘open’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8376: error: ‘struct net_device’ has no member named ‘stop’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8377: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8378: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_wx_set_freq’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8517: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8523: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_pci_probe’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8870: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8872: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8897: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8898: error: ‘struct net_device’ has no member named ‘open’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8899: error: ‘struct net_device’ has no member named ‘stop’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8900: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8901: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8902: error: ‘ARPHRD_IEEE80211’ undeclared (first use in this function)
make[2]: *** [/home/ubuntugod/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/ubuntugod/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [modules] Error 2
-------------------------------------------------------------------------------------------

---

### Post by psychok7 on 2010-02-08
> **zach_kirov said:**
> Hi I followed the instruction in [http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG](http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG)
When I do until the "make" step, I get an error like this. I have tried to use 'make SHELL=/bin/bash' and I got the same error too. May I know what is the problem please? 

-------------------------------------------------------------------------------------------
ubuntugod@ubuntu:~/ipwraw-ng$ sudo make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.31-16-generic/build M=/home/ubuntugod/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/ubuntugod/ipwraw-ng/ipwraw.o
/home/ubuntugod/ipwraw-ng/ipwraw.c:43:27: error: net/ieee80211.h: No such file or directory
In file included from /home/ubuntugod/ipwraw-ng/ipwraw.h:51,
                 from /home/ubuntugod/ipwraw-ng/ipwraw.c:48:
/home/ubuntugod/ipwraw-ng/iwlwifi_hw.h:525: error: array type has incomplete element type
/home/ubuntugod/ipwraw-ng/iwlwifi_hw.h:847: error: array type has incomplete element type
In file included from /home/ubuntugod/ipwraw-ng/ipwraw.c:48:
/home/ubuntugod/ipwraw-ng/ipwraw.h:531: error: field ‘frame’ has incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.h:532: error: ‘IEEE80211_FRAME_LEN’ undeclared here (not in a function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘frame_get_hdrlen’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: ‘IEEE80211_3ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: (Each undeclared identifier is reported only once
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: for each function it appears in.)
/home/ubuntugod/ipwraw-ng/ipwraw.c:53: error: implicit declaration of function ‘WLAN_FC_GET_STYPE’
/home/ubuntugod/ipwraw-ng/ipwraw.c:55: error: implicit declaration of function ‘WLAN_FC_GET_TYPE’
/home/ubuntugod/ipwraw-ng/ipwraw.c:56: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_FROMDS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_TODS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:58: error: ‘IEEE80211_4ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:59: error: ‘IEEE80211_STYPE_QOS_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:62: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:64: error: ‘IEEE80211_STYPE_CTS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:65: error: ‘IEEE80211_STYPE_ACK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:66: error: ‘IEEE80211_1ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:69: error: ‘IEEE80211_2ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_channel_a_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1709: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_channel_bg_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1714: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘store_channel’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1878: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:1884: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘store_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1926: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:1927: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_get_channel_info’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:3284: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:3294: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘reg_get_chnl_grp_index’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:3489: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_init_channel_map’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:4111: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4112: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_post_alive_work’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:4248: error: ‘IEEE80211_OFDM_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4249: error: ‘IEEE80211_OFDM_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4250: error: ‘IEEE80211_CCK_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4251: error: ‘IEEE80211_CCK_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_queue_tx_free_tfd’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:5974: error: implicit declaration of function ‘ieee80211_get_hdrlen’
/home/ubuntugod/ipwraw-ng/ipwraw.c:5974: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘raw_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6396: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6406: error: ‘ETH_P_80211_RAW’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6416: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c:6416: warning: its scope is only this definition or declaration, which is probably not what you want
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_data_packet’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6441: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6456: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_duplicate_packet’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6458: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6459: error: implicit declaration of function ‘WLAN_GET_SEQ_SEQ’
/home/ubuntugod/ipwraw-ng/ipwraw.c:6460: error: implicit declaration of function ‘WLAN_GET_SEQ_FRAG’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_tx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6509: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6509: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6514: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6514: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6522: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6526: error: ‘IEEE80211_RADIOTAP_HDRLEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6540: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6563: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6623: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6623: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6628: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6628: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6646: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_reply_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: error: variable ‘stats’ has initializer but incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: error: unknown field ‘rssi’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: error: unknown field ‘signal’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: error: unknown field ‘noise’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: error: unknown field ‘mac_time’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: error: unknown field ‘rate’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: error: unknown field ‘received_channel’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: error: unknown field ‘len’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6860: error: unknown field ‘freq’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: error: unknown field ‘tsf’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: error: unknown field ‘beacon_time’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: error: storage size of ‘stats’ isn’t known
/home/ubuntugod/ipwraw-ng/ipwraw.c:6881: error: ‘IEEE80211_STATMASK_RSSI’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6885: error: ‘IEEE80211_STATMASK_SIGNAL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6887: error: ‘IEEE80211_STATMASK_NOISE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6889: error: ‘IEEE80211_STATMASK_RATE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: warning: unused variable ‘stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7256: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_rate’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7263: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7264: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7295: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7302: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7303: error: ‘IEEE80211_STYPE_AUTH’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7304: error: ‘IEEE80211_STYPE_DEAUTH’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7305: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7306: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7333: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_basic’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7340: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7340: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7341: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7345: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7354: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7354: error: ‘IEEE80211_FCTL_MOREFRAGS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7359: error: ‘IEEE80211_FCS_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7366: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7366: error: ‘IEEE80211_FCTL_PROTECTED’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7382: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7383: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7384: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7385: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7386: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘tx_skb’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7420: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7422: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7423: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7430: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7439: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7491: warning: passing argument 3 of ‘ipw_build_tx_cmd_basic’ from incompatible pointer type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7330: note: expected ‘struct ieee80211_hdr_4addr *’ but argument is of type ‘struct ieee80211_hdr_4addr *’
/home/ubuntugod/ipwraw-ng/ipwraw.c:7493: warning: passing argument 3 of ‘ipw_build_tx_cmd_rate’ from incompatible pointer type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7253: note: expected ‘struct ieee80211_hdr_4addr *’ but argument is of type ‘struct ieee80211_hdr_4addr *’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_net_hard_start_xmit’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7562: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_hdr_1addr’ 
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7582: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7583: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7586: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_prom_alloc’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8374: error: ‘ARPHRD_IEEE80211_RADIOTAP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8375: error: ‘struct net_device’ has no member named ‘open’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8376: error: ‘struct net_device’ has no member named ‘stop’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8377: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8378: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_wx_set_freq’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8517: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8523: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_pci_probe’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8870: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8872: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8897: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8898: error: ‘struct net_device’ has no member named ‘open’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8899: error: ‘struct net_device’ has no member named ‘stop’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8900: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8901: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8902: error: ‘ARPHRD_IEEE80211’ undeclared (first use in this function)
make[2]: *** [/home/ubuntugod/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/ubuntugod/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [modules] Error 2
-------------------------------------------------------------------------------------------

got the exact same problem.. can someone help? using karmic

---

### Post by chili555 on 2010-02-08
> got the exact same problem.. can someone help? using karmicI believe this file, ipraw, was built in February, 2008. It's probably too old for the Karmic kernel.

---

### Post by rudolfius on 2010-03-25
I have got exactly same error .... please give us any solutions pleasee ... Thank you:popcorn:

---

### Post by ivanatora on 2010-04-14
And another one with the same `make` error. Tried with older source of ipwraw - same there.

---

### Post by chili555 on 2010-04-14
If you have the packages *build-essential* and *linux-headers-generic *installed and it still errors out, then I suggest you ask the developers of ipraw-ng why their package won't compile.

---

### Post by johnk396 on 2010-05-24
I am also getting the same error and am wondering if anyone has figured out the problem.

---

### Post by layers on 2011-02-25
nvm, I wasn't using mon3, which was created by airmon-ng start wlan0

---

### Post by Kind_Man on 2011-09-06
I was reading the post regarding the PRO/Wireless  3945ABG Wireless Card, and trying all the steps, I don't know things  seem not right
before I proceed, I'm new to Ubuntu
but I have idea about commands I used to work with DOS stuff
I installed Ubuntu 10.04 LTS

---

### Post by chili555 on 2011-09-15
I'm sorry. I have no knowledge of patches for injection.

---

