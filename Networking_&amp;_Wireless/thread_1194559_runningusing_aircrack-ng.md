---
title: "running/using aircrack-ng"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by arn36 on 2009-06-22
hello,[INDENT]i am a complete noob to ubuntu and linux.  I am tryin to use aircrack-ng.  I installed it and attempted to run in via the terminal.  Im not sure if i did it correctly. I typed aircrack-ng as a command in the terminal and im lost from there. below is what im seeing on my screen. Please help. Thank you very much.  

arn36@ubuntu:~$ aircrack-ng

  Aircrack-ng 1.0 rc3 - (C) 2006, 2007, 2008, 2009 Thomas d'Otreppe
  Original work: Christophe Devine
  [http://www.aircrack-ng.org](http://www.aircrack-ng.org)

  usage: aircrack-ng [options] <.cap / .ivs file(s)>

  Common options:

      -a <amode> : force attack mode (1/WEP, 2/WPA-PSK)
      -e <essid> : target selection: network identifier
      -b <bssid> : target selection: access point's MAC
      -p <nbcpu> : # of CPU to use  (default: all CPUs)
      -q         : enable quiet mode (no status output)
      -C <macs>  : merge the given APs to a virtual one
      -l <file>  : write key to file

  Static WEP cracking options:

      -c         : search alpha-numeric characters only
      -t         : search binary coded decimal chr only
      -h         : search the numeric key for Fritz!BOX
      -d <mask>  : use masking of the key (A1:XX:CF:YY)
      -m <maddr> : MAC address to filter usable packets
      -n <nbits> : WEP key length :  64/128/152/256/512
      -i <index> : WEP key index (1 to 4), default: any
      -f <fudge> : bruteforce fudge factor,  default: 2
      -k <korek> : disable one attack method  (1 to 17)
      -x or -x0  : disable bruteforce for last keybytes
      -x1        : last keybyte bruteforcing  (default)
      -x2        : enable last  2 keybytes bruteforcing
      -X         : disable  bruteforce   multithreading
      -y         : experimental  single bruteforce mode
      -K         : use only old KoreK attacks (pre-PTW)
      -s         : show the key in ASCII while cracking
      -M <num>   : specify maximum number of IVs to use
      -D         : WEP decloak, skips broken keystreams
      -P <num>   : PTW debug:  1: disable Klein, 2: PTW
      -1         : run only 1 try to crack key with PTW

  WEP and WPA-PSK cracking options:

      -w <words> : path to wordlist(s) filename(s)

      --help     : Displays this usage screen

No file to crack specified.

[/INDENT]

---

### Post by arn36 on 2009-06-22
hello,i am a complete noob to ubuntu and linux. I am tryin to use aircrack-ng. I installed it and attempted to run in via the terminal. Im not sure if i did it correctly. I typed aircrack-ng as a command in the terminal and im lost from there. below is what im seeing on my screen. Please help. Thank you very much. 

arn36@ubuntu:~$ aircrack-ng

  Aircrack-ng 1.0 rc3 - (C) 2006, 2007, 2008, 2009 Thomas d'Otreppe
  Original work: Christophe Devine
  [http://www.aircrack-ng.org]("http://www.aircrack-ng.org/")

  usage: aircrack-ng [options] <.cap / .ivs file(s)>

  Common options:

      -a <amode> : force attack mode (1/WEP, 2/WPA-PSK)
      -e <essid> : target selection: network identifier
      -b <bssid> : target selection: access point's MAC
      -p <nbcpu> : # of CPU to use  (default: all CPUs)
      -q         : enable quiet mode (no status output)
      -C <macs>  : merge the given APs to a virtual one
      -l <file>  : write key to file

  Static WEP cracking options:

      -c         : search alpha-numeric characters only
      -t         : search binary coded decimal chr only
      -h         : search the numeric key for Fritz!BOX
      -d <mask>  : use masking of the key (A1:XX:CF:YY)
      -m <maddr> : MAC address to filter usable packets
      -n <nbits> : WEP key length :  64/128/152/256/512
      -i <index> : WEP key index (1 to 4), default: any
      -f <fudge> : bruteforce fudge factor,  default: 2
      -k <korek> : disable one attack method  (1 to 17)
      -x or -x0  : disable bruteforce for last keybytes
      -x1        : last keybyte bruteforcing  (default)
      -x2        : enable last  2 keybytes bruteforcing
      -X         : disable  bruteforce   multithreading
      -y         : experimental  single bruteforce mode
      -K         : use only old KoreK attacks (pre-PTW)
      -s         : show the key in ASCII while cracking
      -M <num>   : specify maximum number of IVs to use
      -D         : WEP decloak, skips broken keystreams
      -P <num>   : PTW debug:  1: disable Klein, 2: PTW
      -1         : run only 1 try to crack key with PTW

  WEP and WPA-PSK cracking options:

      -w <words> : path to wordlist(s) filename(s)

      --help     : Displays this usage screen

No file to crack specified.

---

### Post by overdrank on 2009-06-22
Hi ans welcome, please do not create multiple threads on the same issue. Threads merged.

---

### Post by ChronoSphere on 2009-07-01
Here's the best guide:

[http://ubuntuforums.org/showthread.php?t=528276&highlight=Aircrack-NG](http://ubuntuforums.org/showthread.php?t=528276&highlight=Aircrack-NG)

---

