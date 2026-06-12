---
title: "Installing soundcard Terratec EWX 24/96"
date: 2010-04-19
forum: Multimedia Software
---

### Post by G-Sun on 2010-04-19
Hi!
I'm new to linux.
Can you help me get my soundcard working?

It's a Terratec EWX 24/96.

It's in the list of supported soundcards:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

But all this command-this-on-terminal is confusing me.

Thanks for all help!

---

### Post by cchhrriiss121212 on 2010-04-19
This is a pci card, so make sure you have your onbaord sound disabled in bios. Check the card is recognised by pasting "aplay -l" into a terminal.

It has an ice1712 chip, which means you can control the levels and set the sample rate using envy24ctl, which is in a package called alsa-tools. If you are using studio , then it is already installed. Go to the tab called analog volume to see the output/input levels.

Are you planning to use this to record with jack?

I have a card with the same chip type, and pulse audio does not work at all well with it, so you may consider un-installing it using synaptic. You can leave it there for now as it won't interfere with setting up jack.

---

### Post by lidex on 2010-04-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

See this:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442")

---

### Post by G-Sun on 2010-04-20
> **cchhrriiss121212 said:**
> This is a pci card, so make sure you have your onbaord sound disabled in bios. Check the card is recognised by pasting "aplay -l" into a terminal.
I'll disabele the onboard card.
The EWX is recoognized

> It has an ice1712 chip, which means you can control the levels and set the sample rate using envy24ctl, which is in a package called alsa-tools. If you are using studio , then it is already installed. Go to the tab called analog volume to see the output/input levels.Where do I find alsa-tools? (I didn't install all the audio-stuff when installing)

> Are you planning to use this to record with jack?Yes, but only for testing now

> I have a card with the same chip type, and pulse audio does not work at all well with it, so you may consider un-installing it using synaptic. You can leave it there for now as it won't interfere with setting up jack.So, why set up jack if the soundcard is not working right?

Thanks!

---

### Post by G-Sun on 2010-04-20
```
uname -a
Linux Solis 2.6.24-27-rt #1 SMP PREEMPT RT Fri Mar 12 03:03:40 UTC 2010 i686 GNU/Linux

``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: EWX2496 [TerraTec EWX24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jan 28 2010 for kernel 2.6.24-27-rt (SMP).
``````

head -n 1 /proc/asound/card*/codec#*
head: kan ikke åpne «/proc/asound/card*/codec#*» for lesing: No such file or directory
```(kan ikke åpne = Can't open ; for lesing = for reading)

Thanks!

---

### Post by G-Sun on 2010-04-20
I've had sound coming out from my EWX.
Only right channel, and distorted in a way..

---

### Post by cchhrriiss121212 on 2010-04-20
> So, why set up jack if the soundcard is not working right?
Most people who buy a recording interface will be using it with jack as it is the best sound server to use with recording programs. Alsa-tools is in synaptic package manager, you could install from the studio dvd or from the repos.

---

### Post by Yellow Pasque on 2010-04-20
Upgrade ALSA. I've customized the ALSA upgrade script ( [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) ) for your setup. After you download, go to the terminal and:

```
cd <wherever you downloaded the file>
chmod a+x AlsaUpgrade-1.0.23.sh
sudo ./AlsaUpgrade-1.0.23.sh -d
sudo ./AlsaUpgrade-1.0.23.sh -c
sudo ./AlsaUpgrade-1.0.23.sh -i
sudo ./AlsaUpgrade-1.0.23.sh -t
```

---

### Post by G-Sun on 2010-04-20
> **Temüjin said:**
> Upgrade ALSA. I've customized the ALSA upgrade script ( [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) ) for your setup. After you download, go to the terminal and:

```
cd <wherever you downloaded the file>
chmod a+x AlsaUpgrade-1.0.23.sh
sudo ./AlsaUpgrade-1.0.23.sh -d
sudo ./AlsaUpgrade-1.0.23.sh -c
sudo ./AlsaUpgrade-1.0.23.sh -i
sudo ./AlsaUpgrade-1.0.23.sh -t
```

Thanks a lot!
Downloaded and ran your code.
This is the result:
```
geir@Solis:~/Nedlastinger$ chmod a+x AlsaUpgrade-1.0.23.sh
geir@Solis:~/Nedlastinger$ sudo ./AlsaUpgrade-1.0.23.sh -d


--ti. 20. april 17:49:15 +0200 2010----Alsa-Upgrade-Script-1.0.23-1 ----------------- 
-
- You'll be upgraded from 1.0.16. to 1.0.23
- Run -h option for further help and to look up the workflows
-
-
-
- 
- DISCLAIMER: Use this script at your own risk. I do not take any 
-             responsability for any problems caused by running 
-             this script. 
-
- In any case I strongly advise you to make a backup first!
--------------------------------------------------------------------------------------
-
-
- Do you want to prepare the environment and download 1.0.23 [y/n]: y

--------------------------------------------------------------------------------------
-  Nothing changed! 
--------------------------------------------------------------------------------------
geir@Solis:~/Nedlastinger$ 

```

---

### Post by G-Sun on 2010-04-20
After disabeling onboard audio in Bios:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: EWX2496 [TerraTec EWX24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by G-Sun on 2010-04-20
I'm able to play 16bit wav-files and get sound in my right speaker..
Sounds right :)

---

### Post by Yellow Pasque on 2010-04-20
Hmm. That's odd that the script doesn't work. You entered y, so it shouldn't output "nothing changed"
```
package () {
echo -n "- Do you want to $1 $PACKAGE [y/n]: " 
   read yesno
   case $yesno in
       		y* | Y*  	) setpack ;;
       		n* | N*         ) header "Nothing changed! " ; exit 0  ;;
       		*	        ) header "Nothing changed! " ; exit 0  ;;
esac
```
Try it again.

---

### Post by G-Sun on 2010-04-20
> **Temüjin said:**
> Hmm. That's odd that the script doesn't work. You entered y, so it shouldn't output "nothing changed"
```
package () {
echo -n "- Do you want to $1 $PACKAGE [y/n]: " 
   read yesno
   case $yesno in
               y* | Y*      ) setpack ;;
               n* | N*         ) header "Nothing changed! " ; exit 0  ;;
               *            ) header "Nothing changed! " ; exit 0  ;;
esac
```Try it again.
Do you mean the same code again, the new code above, or..?

---

### Post by G-Sun on 2010-04-21
Went into Gnome Alasa-mixer and fixed a half muted left channel.
So now I have:
- Stereo output
- Can play many file-types, a little unsure if I can play mp3s..

Havn't tested ADC st. in,
and wonder if digital in/out is gonna work.

---

### Post by G-Sun on 2010-04-21
Ok, I prgressed and got sound:
Soundcard > Jack > Ardour > Jack > Soundcard.
I lttle trubbel with the levels, guess it's something about +4 or -10db.
I'm not sure yet if the sound is clean/right.
I wasn't convinced by what I heard, but I'll check again with a better mic.

---

### Post by G-Sun on 2010-04-25
There seems to be an isssue:
I had my EWX-card showing up in Jack/Connections but now it's gone.
And I can't play mp3s in Totem,
but mp3s in Firfox is fine.

Any ideas?

---

### Post by G-Sun on 2010-04-30
Installed Ubuntu 10.04 and upgraded to Ubuntu Studio 10.04 as suggested on this page:
[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

No sound, what to do again?

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: EWX2496 [TerraTec EWX24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```and I didn't manage to add myself to the audio user group. So jack is giving me an error..

---

### Post by lidex on 2010-04-30
Try this:
> Alternate channel mappings needed for ICE1712

Cards such as Audiophile 2496, Delta 1010LT and others using the ICE1712 chip, there is a bug with the channel mapping.

Diagnosis

Open a terminal, then enter this command:

cat /proc/asound/cards | grep ICE1712

If you get a line specifying the name of your soundcard, you're probably affected.

Fix / workaround

See [bug #178442]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442"). 

---

### Post by G-Sun on 2010-05-01
Thanks! So, is this where I have to manually configure my soundcard:

/etc/pulse/default.pa:
```
# Load Delta 44:
load-module module-alsa-sink sink_name=delta_out device=hw:1 channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
load-module module-alsa-source source_name=delta_in device=hw:1 channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
```Where I swap Delta 44 with EWX 24/96 and my configuration.
So what will that be? 
Something like: 
```

# Load Terratec EWX 24/96:
load-module module-alsa-sink sink_name=ewx2496_out device=hw:1 channels=4 channel_map=analog-left,analog-right,digital-left, digital-right
load-module module-alsa-source source_name=ewx2496_in device=hw:1 channels=4 channel_map=analog-left,analog-right,digital-left, digital-right

```?
Or, should it be hw:0  ?

---

### Post by G-Sun on 2010-05-01
And then I comment out this section?
```
### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif
```

---

### Post by G-Sun on 2010-05-02
I've changed the /etc/pulse/default.pa
to:
```
# Load Terratec EWX 24/96:
load-module module-alsa-sink sink_name=ewx2496_out device=hw:1 channels=4 channel_map=left,right,digital-left,digital-right
load-module module-alsa-source source_name=ewx2496_in device=hw:1 channels=4 channel_map=left,right,digital-left,digital-right

### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
#load-module module-detect
#.endif
```But no success.

Jack says:
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]17:56:38.104 JACK was started with PID=19245.[/COLOR]
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    769824
 no message buffer overruns
 JACK compiled with System V SHM support.
 `default' server already active
 [COLOR=#999999]17:56:38.370 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]17:56:38.371 Post-shutdown script...[/COLOR]
 [COLOR=#990099]17:56:38.372 killall jackd[/COLOR]
 [COLOR=#999999]17:56:38.822 Post-shutdown script terminated successfully.[/COLOR]
 [COLOR=#ff0000]17:56:40.304 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```

---

### Post by G-Sun on 2010-05-02
And yes:
```
cat /proc/asound/cards | grep ICE1712
 0 [EWX2496        ]: ICE1712 - TerraTec EWX24/96

```

---

### Post by G-Sun on 2010-05-02
In dafault.pa
it says:
```
# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)
```So, maybe it is system.pa I should edit?

---

### Post by G-Sun on 2010-05-02
I tried another solution as described here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

```

**sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release  -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo  apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated  install medibuntu-keyring; sudo apt-get -q update**
```But no success

---

### Post by cchhrriiss121212 on 2010-05-02
You might be making this more complicated than it needs to be. Have you considered just removing pulse audio? It seems to be the source of trouble here, and without it all the applications you need will run with alsa.

---

### Post by G-Sun on 2010-05-02
> **cchhrriiss121212 said:**
> You might be making this more complicated than it needs to be. Have you considered just removing pulse audio? It seems to be the source of trouble here, and without it all the applications you need will run with alsa.
ok :) I thought pulse was needed..

---

### Post by G-Sun on 2010-05-02
Removed pulse with the connected components.
Jack started fine, but my soundcard doesn't show up in connections > Audio
Not able to get any sound..

---

### Post by lidex on 2010-05-02
These may help:
[http://ubuntuforums.org/showthread.php?t=806730]("http://ubuntuforums.org/showthread.php?t=806730")
[http://swiss.ubuntuforums.org/showthread.php?p=8562193]("http://swiss.ubuntuforums.org/showthread.php?p=8562193")

---

### Post by G-Sun on 2010-05-02
Correction:
I have systemsounds playing :)
(had to log off and in again)
But nothing else yet.

---

### Post by G-Sun on 2010-05-03
Update: I have sound in browser when using YouTube
But nothing when playing sound-files directly in browser

---

### Post by Yellow Pasque on 2010-05-03
At this point, I really can't tell what you've done, but I will point out that the apps you have sound in are apps that use ALSA directly, i.e. Flash/YouTube and event sounds/libcanberra. If you completely removed pulseaudio, maybe you just need to configure the rest of your apps to use ALSA.

---

### Post by cchhrriiss121212 on 2010-05-03
I tried a fresh install this morning and the following steps were all I needed to do:
Remove pulse
Set output levels
Reboot
Which programs are not playing audio?

---

### Post by rvperez on 2011-01-21
I have also a terratec EWX 24/96.
I have installed ubuntu 7.04, and xubuntu 9.00 and at the end 10.04, my sound card Terratec works fine in 7.04 and 9.00 without any configuration works fine as default instalation, but in 10.04 doesn't work as default, then I installed alsa components, and I only can play I can't record, the input it doesn't work I can't use my skype account because I can't speak, I only can ear. Then I try install pulse components in order to can work with inputs. At the end I can't ear and record. I can't ear music now. I tried instal unistall components with install with "centro de software ubuntu" ("ubuntu software center" I guess that it is the translation in english, I have installed the spanish version).

Could you help me?

---

### Post by rvperez on 2011-01-21
cat /proc/asound/cards | grep ICE1712
ric@ric-desktop:~$ cat /proc/asound/cards | grep ICE1712
 0 [EWX2496        ]: ICE1712 - TerraTec EWX24/96
ric@ric-desktop:~$ uname -a
Linux ric-desktop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux
ric@ric-desktop:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: EWX2496 [TerraTec EWX24/96], dispositivo 0: ICE1712 multi [ICE1712 multi]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
ric@ric-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
ric@ric-desktop:~$ head -n 1 /proc/asound/card*/codec#*
head: no se puede abrir «/proc/asound/card*/codec#*» para lectura: No existe el archivo o directorio

---

### Post by rvperez on 2011-01-21
thanks

---

### Post by lidex on 2011-01-22
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by G-Sun on 2011-01-22
Please tell us if you succeed and what eventually worked for you :)
Good luck!

---

### Post by rvperez on 2011-01-29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: solicitando clave 72B194E5 de hkp servidor keyserver.ubuntu.com
gpg: clave 72B194E5: clave pública "Launchpad Ubuntu Audio Dev team PPA" importada
gpg: Cantidad total procesada: 1
gpg:               importadas: 1  (RSA: 1)
ric@ric-desktop:~$ sudo apt-get update
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid Release.gpg
Des:1 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/main Translation-es [658kB]   
Des:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) lucid/main Translation-es
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-es      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-es
Des:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14,0kB]                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-es  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-es
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Des:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [5346B]      
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources      
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources  
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Des:5 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-es [2779B]
Des:6 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/universe Translation-es [1393kB]
Des:7 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-es [99,0kB]
Des:8 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates Release.gpg [198B]     
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-es
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-es
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-es
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid Release
Des:9 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates Release [44,7kB]              
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/main Packages                           
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/main Sources      
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/universe Packages 
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/universe Sources  
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid/multiverse Sources
Des:10 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/main Packages [436kB]
Des:11 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/restricted Packages [3240B]
Des:12 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/main Sources [177kB]
Des:13 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/restricted Sources [1443B]
Des:14 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/universe Packages [181kB]
Des:15 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/universe Sources [64,8kB]
Des:16 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/multiverse Packages [8436B]
Des:17 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) lucid-updates/multiverse Sources [4372B]
Descargados 3094kB en 12s (248kB/s)                                            
Leyendo lista de paquetes... Hecho
ric@ric-desktop:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete linux-alsa-driver-modules-2.6.32-28-generic
ric@ric-desktop:~$ 

It can't find the packet linux-alsa-driver-modules-2.6.32-28-generic

thanks

---

### Post by rvperez on 2011-02-02
Could somebody help me?

thank you

---

### Post by lidex on 2011-02-02
The alsa modules for 2.6.32-28 should be out now, try again:
```
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

---

### Post by rvperez on 2011-02-04
none the xubuntu see the app that should be playing but the bar don't increase the time.

The play button is pressed but don't sound, the video player also stop when I tried play, but the frame is frezed, with the first picture.

Thanks

---

### Post by rvperez on 2011-02-04
I updated also before:

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Feb  4 2011 for kernel 2.6.32-28-generic (SMP).

---

### Post by rvperez on 2011-02-14
none

---

### Post by rvperez on 2011-02-14
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Feb 13 2011 for kernel 2.6.32-28-generic (SMP).

---

### Post by rvperez on 2011-02-15
Now the video player and audio player run, the bar  and time increase the video, and audio read and show playing the media files but none sound

Please could somebody help me

Thanks

---

### Post by rvperez on 2011-02-17
no sound and now no play again the video player

---

### Post by rvperez on 2011-03-12
I send a capture I updated the alsa but again ask for the update again, it semm like don't can't write the update in the computer because the udate request appear again, but not in the same day.

---

### Post by lidex on 2011-03-17
May need to start from scratch. 
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

