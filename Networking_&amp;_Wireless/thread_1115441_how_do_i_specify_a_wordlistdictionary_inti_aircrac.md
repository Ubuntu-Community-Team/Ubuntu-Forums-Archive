---
title: "how do i specify a wordlist/dictionary inti aircrack-ng"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-04-03
I use this command when testing my own WPA-PSK Network.

I am unsure how to implement a dictionary/wordlist for the bellow command to check against.

I have downloaded a wordlist called wpa.txt to my desktop.
And I need to specify the full path to it in the bellow command.

How can I do this??

@ubuntu:~$ sudo aircrack-ng -w password.lst(this is where I need to specify the full path to he downloaded twpa.txt) -b 00:00:00:00:00:00 psk*.cap

[sudo] password for mark: 
fopen(dictionary) failed: No such file or directory
fopen(dictionary) failed: No such file or directory
Opening psk-01.cap
Opening psk-02.cap
Opening psk-03.cap
Opening psk-04.cap
Opening psk-05.cap
Opening psk-06.cap
Opening psk-07.cap
Opening psk-08.cap
Opening psk-09.cap
Opening psk-10.cap
Opening psk-11.cap
Opening psk-12.cap
Opening psk-13.cap
Please specify a dictionary (option -w).

---

### Post by scrypt on 2009-04-04
CH  9 ][ Elapsed: 50 mins ][ 2009-04-04 05:58 ][ WPA handshake: 00:     
  00:00:00:00:00                                                                                     
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ESSID
                                                                                       
 00:00:00:00:00    0  96    29225      704    0   9  54  WPA  TKIP   PSK  *********  
                                                                                       
 BSSID              STATION            PWR   Rate  Lost  Packets  Probes               
                                                                                       
 00:00:00:00:00  00:00:00:00:00    0   0- 0     0     1222                 

\\i have established a fourway handshake as you can see but i cannot workout how to add a dictionary/wordlist to a command  to to use for the wordlist scan

\\\here s the command i need to run :

 sudo aircrack-ng -w password.lst -b 00:14:6C:7E:40:80 psk*.cap

where it says password.lst I nned to add the full path of my downloaded wordfile/ dictionary.

This is where i am stuck

can anybody give me clear consice step by step instructions on how i do this please???

---

### Post by scrypt on 2009-04-04
Any more help would be appreciated


this is the command i ned to use and as you can see i have entered the path to the wpa wordlist i have downloaded and even added my wpa-psk passphrase into it. so i know that my passphrase is there %100

 sudo  aircrack-ng -w '/home/mark/Desktop/wpa.txt'  -b 00:1E:74:6C:22:96 psk*.cap psk*.cap

But I am getting this error :-

Opening psk-14.cap
Opening psk-15.cap
Opening psk-16.cap
Opening psk-17.cap
Opening psk-18.cap
Opening psk-19.cap
Opening psk-20.cap
Opening psk-21.cap
Opening psk-22.cap

Invalid packet capture length 0 - corrupted file?

why is this.

where are all the clever people when i need em??

---

### Post by scrypt on 2009-04-04
Have I entered in the right full path to the downloaded wpa wordlist i downloaded and the extracted to my desktop??

---

### Post by scrypt on 2009-04-04
Bump

---

### Post by scrypt on 2009-04-04
I have downloaded a wordlist to my Desktop called wpa.txt

I need to add this to the below command using the full path

Im not above admiting that I don't get it??

I have tried this :

 sudo aircrack-ng -w /home/mark/Desktop/wpa.txt -b 00:00:00:00:00:00 psk*.cap

And this :

 sudo aircrack-ng -w ~/Desktop/wpa.txt -b 00:00:00:00:00:00  psk*.cap

But it's just not having any of it? I have searched hard for an answer. with no luck.

All I get is this no matter what I do:

Opening psk-14.cap
Opening psk-15.cap
Opening psk-16.cap
Opening psk-17.cap
Opening psk-18.cap
Opening psk-19.cap
Opening psk-20.cap
Opening psk-21.cap
Opening psk-22.cap

Invalid packet capture length 0 - corrupted file?

Can you see where I'm going wrong?


HELP

---

### Post by scrypt on 2009-04-04
what would be the correct full path to the wpa.txt file that is situated on my Desktop?

---

### Post by scrypt on 2009-04-04
No worries I solved this myself.

Here is the command i used:-

mark@ubuntu:~$ sudo aircrack-ng wpascrypt-01.cap -w /home/mark/Desktop/wpa3.txt
Opening wpascrypt-01.cap
Read 481569 packets.

where wpascrypt-01.cap is the file i created to keep the caught packets in.

This is the command i used to check that the file wpascrypt-01.cap did succesfuly contain the capture packet.

mark@ubuntu:~$ sudo aircrack-ng wpascrypt-01.cap
Opening wpascrypt-01.cap
Read 12459 packets.

   #  BSSID              ESSID                     Encryption

   1  00:00:00:00:00:00  N.O.R                    WPA (1 handshake)

Choosing first network as target.

Opening wpascrypt-01.cap
Please specify a dictionary (option -w).


Quitting aircrack-ng...
 

So when I ran this command:-

mark@ubuntu:~$ sudo aircrack-ng wpascrypt-01.cap -w /home/mark/Desktop/wpa3.txt

it succesfully scanned the wordlist i downloaded and added my routers passphrase to called wpa3.txt.

SORTED

---

### Post by scrypt on 2009-04-04
Trouble was that the wordlist i downloaded.

aicrack was not recognizing its file type.

originally it was a.rar file which i extracted to my desktop.
 
But when i re-downloaded the original .rar file and the re-extracted it to my desktop again and deleted the original one.

 The aicrack command recognised it as  a suitable file type this time.

this was the command i used stating the full path to my downloaded wordlist:-

mark@ubuntu:~$ sudo aircrack-ng wpascrypt-01.cap -w /home/mark/Desktop/wpa3.txt
Opening wpascrypt-01.cap
Read 481569 packets.

---

### Post by scrypt on 2009-04-04
@ubuntu:~$ sudo aircrack-ng -w /home/mark/Desktop/wordlist.txt -b 00:00:00:00:00:00 psk*.cap

the psk*.cap need to the file i originally created to keep the captured packets in ie wpa-01.cap

So to quickly clarify something. For example wpa-01.cap is the where the captured packets are being kept once capture.

So each time you run the corresponding Aircrack caommand a new wpa.cap file will be created.
ie. wpa-01.cap
    wpa-02.cap
    wpa-03.cap

So as long as captured packets are successfuly captured in wpa-01.cap

this is the file u need to run airacrack (or your own) wordlist/dictionary against.

---

### Post by mbuller10 on 2009-05-11
hey no one else has replied or appreciates this but I do man thanks

---

### Post by scrypt on 2010-03-23
Glad that somebody found use with my post.

My above posts are for educational purposes only

Scrypt

---

### Post by a_petrov303 on 2010-06-03
where can one find a good word list?

---

### Post by Doctadrez on 2010-06-03
google search for a word list.

Or check out the church of wifi.

---

### Post by Iowan on 2010-06-03
Closed
Although aircrack might be used to test one's own network, the potential for abuse is quite high. Other forums can provide the necessary information.

---

