---
title: "ssh and; WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by ozguitarplayer on 2009-09-14
Hi,
I am fairly new to Linux systems.
I have 4 computers all Ubuntu (3 x Hardy & 1 x Jackalope)


Yesterday I networked them with ssh and all was good.
The IP's were;
192.168.1.101 MasterJack
192.168.1.102 MasterHeron
192.168.1.103 MusicHeron
192.168.1.104 magz_laptop


This is the /etc/hosts entry that I made;

127.0.0.1	localhost
127.0.1.1	MasterJack

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.102 Debian
192.168.1.103 MusicHeron
192.168.1.104 magz_laptop

Today when I tried to connect I found that 103 and 104 have reversed their IP addresses and I now cannot connect to either of them with ssh with gui or ssh in termimal.
(I haven't learned how to put this info into the little boxes that others use) however this is the output trying to connect with one of the computers;

nigel@MasterJack:~$ ssh 192.168.1.103
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f8:f7:27:62:3a:86:70:79:36:79:0d:cc:5a:12:45:e2.
Please contact your system administrator.
Add correct host key in /home/nigel/.ssh/known_hosts to get rid of this message.
Offending key in /home/nigel/.ssh/known_hosts:2
RSA host key for 192.168.1.103 has changed and you have requested strict checking.
Host key verification failed.
nigel@MasterJack:~$ 

I am told to add the correct host key to /home/nigel/.ssh/known_hosts
This is how /home/nigel/.ssh/known_hosts reads.  

|1|SxAnnrbcfEjwOFVdiGchZCHtefQ=|Mt4n3ZJ7meMz7ERD3K4dtpa/xXo= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA2WDq2HqqSBQwMmJ8Vx9P2hyy0hNwH0QWCNoZY6iz
Dx5AqEpvPcc0+odNcsl7n8jBC4XlEuUSBMYxMWxQSkdabhD/k+oSwtrPNuQERS6tq81j
5AcIPGdC18suuIm3WNQQV4Sm6+5HieyALMbkNqSGZjQ2ZlqWS7L43cyI7PGT1cgK7xt1
D/fplRzRWUPyR/gQ8XKjr4VmKzZaY+6ceFz5E9wbZ1mRLi1Wueun70ITxooJ6m5SvK6h1BRgb6Kqes1GD
R5gADfshjeI60wZREUP8M307Y3nXL1zKOkw9oqZvuXAfvNwOud7dGqjAzcSm4tigsRft
d0u8CJMDOXU7enQPQ==
|1|fxUtlJSqoN75lxZeumcmqHCLRRk=|rBWCXK5DI+/xdoXHRQ360HwP7/s= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA8fL2BhhHBGGN76dULLY8RTEWFEs/vx1dGREQMCoLZ
lT9pOA/lRyT3VC32Z4wUscERieFrjYKx3CHKZ5XNRPGajya61Y1NZjOAZrHWe8fske21W
IRI+rrdlJnHejZqAiyBQR4mAGtHyl8EqfcpU9jVypH/mWtQhv5fAKgoO917q8uLeNh4CI
zmiF1aTsdaZ8vGNS7udGf2+2zXJ9qsu7rSM9YFFFyzcE/E+Li7Grx5lPfwyluLjOSlNNX
aeH904oa3nzo+D1YvontcHJEIjT4exZr15jKEizCqE1rwikRhSDxY9bhi0TrUynvIrKfC
pRa+VnskXV/CEBdqmEJ2v5VUQ==
|1|bV56uZjpfPqlgCLdE3Ik4myaV3k=|qHXU5ska0txpncR1ciDxvxB4M9M= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA2WDq2HqqSBQwMmJ8Vx9P2hyy0hNwH0QWCNoZY6izD
x5AqEpvPcc0+odNcsl7n8jBC4XlEuUSBMYxMWxQSkdabhD/k+oSwtrPNuQERS6tq81j5A
cIPGdC18suuIm3WNQQV4Sm6+5HieyALMbkNqSGZjQ2ZlqWS7L43cyI7PGT1cgK7xt1D/f
plRzRWUPyR/gQ8XKjr4VmKzZaY+6ceFz5E9wbZ1mRLi1Wueun70ITxooJ6m5SvK6h1BRg
b6Kqes1GDR5gADfshjeI60wZREUP8M307Y3nXL1zKOkw9oqZvuXAfvNwOud7dGqjAzcSm
4tigsRftd0u8CJMDOXU7enQPQ==
|1|0sCY0mJjuuMCs6ekOSazIvmDd3k=|NPL98gs1vqkqM1UhCGPur4AjDSE= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA8fL2BhhHBGGN76dULLY8RTEWFEs/vx1dGREQMCoLZ
lT9pOA/lRyT3VC32Z4wUscERieFrjYKx3CHKZ5XNRPGajya61Y1NZjOAZrHWe8fske21WI
RI+rrdlJnHejZqAiyBQR4mAGtHyl8EqfcpU9jVypH/mWtQhv5fAKgoO917q8uLeNh4CIzm
iF1aTsdaZ8vGNS7udGf2+2zXJ9qsu7rSM9YFFFyzcE/E+Li7Grx5lPfwyluLjOSlNNXaeH
904oa3nzo+D1YvontcHJEIjT4exZr15jKEizCqE1rwikRhSDxY9bhi0TrUynvIrKfCpRa
VnskXV/CEBdqmEJ2v5VUQ==|1|1HDptzjL7f6tyF1YfDMLtGdid8M=|x02DVKnbY7l0Xd
mB5Bl+guPxQkg=sshrsaAAAAB3NzaC1yc2EAAAABIwAAAQEAlZaHE3+wWzWZ+TMs23wUrk
2zGP55FRvXXzkGlzE7PGpvTLmpYsRm0eu5K3bQiH6FF4KzampwBZyRLGll44Posurst/87b
1p8Bqv+V8b7fnlX4okrN1UlVWFXAasoNbZrrRGTcs8f6l0B2ZD+w0R4KeimufKiLI/6A1AB
3yD3AUevRxs1TKHJ/mEVFiJLonfmKM9qK1iDTX5LJD7E3RR54FOiybHC2FNrfDdsls51qlv
0hqRf9ixIGkf9RqgbaD3l4pE5VU3ytmN7Wv5+7zXfytY313mHTqlvfSL1rdsq6+4j+8xDW
zoLPxSVkErvXv8u1Op7l0ZoOaENNtmG4Q9ouQ==
|1|xHHyaX8RKN8/nfolCUiUxYuLl8E=|m9tD4kCfZSZPHKqnq2YEvgqnKng= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAlZaHE3+wWzWZ+TMs23wUrk2zGP55FRvXXzkGlzE7PGp
vTLmpYsRm0eu5K3bQiH6FF4KzampwBZyRLGll44Posurst/87b1p8Bqv+V8b7fnlX4okrN1
UlVWFXAasoNbZrrRGTcs8f6l0B2ZD+w0R4KeimufKiLI/6A1AB3yD3AUevRxs1TKHJ/mEVFiJLonfmKM9qK1iDTX5LJD7E3RR54FOiybHC2FNrfDdsls51qlv0hqRf9ixIGkf9Rq
gbaD3l4pE5VU3ytmN7Wv5+7zXfytY313mHTqlvfSL1rdsq6+4j+8xDWzoLPxSVkErvXv8u
1Op7l0ZoOaENNtmG4Q9ouQ==

Maybe this means something to someone, not to me.

Any help sorting this out will be greatly appreciated.

---

### Post by shredder12 on 2009-09-14
I think the problem is that when you ssh your computer tries to match the host key received now but since it doesn't match with the one saved in your ~/.ssh/known_hosts file the connection is not made..

You may try to create a backup of that known_hosts file and then delete the actual one...
This time when you try to ssh a new file will be created and there will be no mismatch as there is no key in the file..

But remember to create a backup, jst in case...

---

### Post by Iowan on 2009-09-14
> **ozguitarplayer said:**
> nigel@MasterJack:~$ ssh 192.168.1.103
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f8:f7:27:62:3a:86:70:79:36:79:0d:cc:5a:12:45:e2.
Please contact your system administrator.
Add correct host key in /home/nigel/.ssh/known_hosts to get rid of this message.
[COLOR="Red"]Offending key in /home/nigel/.ssh/known_hosts:2[/COLOR]
RSA host key for 192.168.1.103 has changed and you have requested strict checking.
Host key verification failed.
nigel@MasterJack:~$ 

I am told to add the correct host key to /home/nigel/.ssh/known_hosts
This is how /home/nigel/.ssh/known_hosts reads.  

|1|SxAnnrbcfEjwOFVdiGchZCHtefQ=|Mt4n3ZJ7meMz7ERD3K4dtpa/xXo= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA2WDq2HqqSBQwMmJ8Vx9P2hyy0hNwH0QWCNoZY6iz
Dx5AqEpvPcc0+odNcsl7n8jBC4XlEuUSBMYxMWxQSkdabhD/k+oSwtrPNuQERS6tq81j
5AcIPGdC18suuIm3WNQQV4Sm6+5HieyALMbkNqSGZjQ2ZlqWS7L43cyI7PGT1cgK7xt1
D/fplRzRWUPyR/gQ8XKjr4VmKzZaY+6ceFz5E9wbZ1mRLi1Wueun70ITxooJ6m5SvK6h1BRgb6Kqes1GD
R5gADfshjeI60wZREUP8M307Y3nXL1zKOkw9oqZvuXAfvNwOud7dGqjAzcSm4tigsRft
d0u8CJMDOXU7enQPQ==
[COLOR="Blue"]|1|fxUtlJSqoN75lxZeumcmqHCLRRk=|rBWCXK5DI+/xdoXHRQ360HwP7/s= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA8fL2BhhHBGGN76dULLY8RTEWFEs/vx1dGREQMCoLZ
lT9pOA/lRyT3VC32Z4wUscERieFrjYKx3CHKZ5XNRPGajya61Y1NZjOAZrHWe8fske21W
IRI+rrdlJnHejZqAiyBQR4mAGtHyl8EqfcpU9jVypH/mWtQhv5fAKgoO917q8uLeNh4CI
zmiF1aTsdaZ8vGNS7udGf2+2zXJ9qsu7rSM9YFFFyzcE/E+Li7Grx5lPfwyluLjOSlNNX
aeH904oa3nzo+D1YvontcHJEIjT4exZr15jKEizCqE1rwikRhSDxY9bhi0TrUynvIrKfC
pRa+VnskXV/CEBdqmEJ2v5VUQ==[/COLOR]
|1|bV56uZjpfPqlgCLdE3Ik4myaV3k=|qHXU5ska0txpncR1ciDxvxB4M9M= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA2WDq2HqqSBQwMmJ8Vx9P2hyy0hNwH0QWCNoZY6izD
x5AqEpvPcc0+odNcsl7n8jBC4XlEuUSBMYxMWxQSkdabhD/k+oSwtrPNuQERS6tq81j5A
cIPGdC18suuIm3WNQQV4Sm6+5HieyALMbkNqSGZjQ2ZlqWS7L43cyI7PGT1cgK7xt1D/f
plRzRWUPyR/gQ8XKjr4VmKzZaY+6ceFz5E9wbZ1mRLi1Wueun70ITxooJ6m5SvK6h1BRg
b6Kqes1GDR5gADfshjeI60wZREUP8M307Y3nXL1zKOkw9oqZvuXAfvNwOud7dGqjAzcSm
4tigsRftd0u8CJMDOXU7enQPQ==
<snip>
|1|xHHyaX8RKN8/nfolCUiUxYuLl8E=|m9tD4kCfZSZPHKqnq2YEvgqnKng= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAlZaHE3+wWzWZ+TMs23wUrk2zGP55FRvXXzkGlzE7PGp
vTLmpYsRm0eu5K3bQiH6FF4KzampwBZyRLGll44Posurst/87b1p8Bqv+V8b7fnlX4okrN1
UlVWFXAasoNbZrrRGTcs8f6l0B2ZD+w0R4KeimufKiLI/6A1AB3yD3AUevRxs1TKHJ/mEVFiJLonfmKM9qK1iDTX5LJD7E3RR54FOiybHC2FNrfDdsls51qlv0hqRf9ixIGkf9Rq
gbaD3l4pE5VU3ytmN7Wv5+7zXfytY313mHTqlvfSL1rdsq6+4j+8xDWzoLPxSVkErvXv8u
1Op7l0ZoOaENNtmG4Q9ouQ==
I recently had this happen when I upgraded a server. In brief, the second entry appears to be the offending key (highlighted in red). I fixed mine by deleting the key (highlighted in blue). A backup (before editing) would seem to be a REALLY good idea.

---

### Post by ozguitarplayer on 2009-09-14
Thanks shredder12 & Iowan,
Your advice was perfect, all is now good.

---

### Post by ozguitarplayer on 2009-09-15
Well I'm back again....
Yesterday morning and again this morning I have failed to connect to my other computers using ssh. 
Thanks to the advice of others I was able to solve the problem, but as it turns out only temporarily, I have to reset information each morning.

I find that the IP addresses I had the day before are no longer the same the next day, sounds weird I know. 

I have change the IP's in /etc/hosts.
For Example:
Yesterday; IP xxx.xxx.x.102  Today needs to be changed to xxx.xxx.x.103
and
Yesterday: IP xxx.xxx.x.103  Today needs to be changed to xxx.xxx.x.102 

If I don't do this I cannot connect to the other networked computers.

Are the IP's assigned by the order that I turn the computers on?
By that I mean if yesterday Computer 3 was turned on last of the three computers it was assigned IP ending .103
And to day if computer 3 was turned on second it is assigned IP ending.102? and therefore there is clash with the order in /etc/hosts?
That's just a wild guess 'cause it doesn't make any sence to me.

Also I have both ssh and sshfs installed, could that be an issue?

Any help please...very confused.

---

### Post by lisati on 2009-09-15
Thought: is using static IPs on the network an option? This might help avoid some of the confusion with IPs changing from day to day.

---

### Post by ozguitarplayer on 2009-09-15
Thanks lisati that sounds good, but how do I make them static?

---

### Post by lisati on 2009-09-15
> **ozguitarplayer said:**
> Thanks lisati that sounds good, but how do I make them static?

I normally tell my router to associate a particular IP with a particular machine (my router uses MAC addresses to identify the machine), other forum users might be able to fill in a few details for the Ubuntu end.

---

### Post by Iowan on 2009-09-15
A couple of ways (or so) - one involves configuring manual address via Network Manager, another requires editing */etc/network/interfaces*, and another moves the responsibility to the DHCP server via static lease. (if the server will handle it).

---

### Post by ozguitarplayer on 2009-09-15
Thanks again lisati I'll search or maybe start a new topic.

---

### Post by ozguitarplayer on 2009-09-15
Hi,
When using ssh to network four Ubuntu computers I find that each morning when I turn them on some of the IP's have reversed i.e.
xxx.xxx.x.102 has become xxx.xxx.x.103 and I have to change the information in /etc/hosts before I cam connect.

I wondered if the order of turning the computers changes the IP's?
I has been suggested that making the IP's static may overcome this issue.
If this is correct, how would I make them static?
Or is there another way to fix the changing IP's?

Any help is appreciated.

---

### Post by ozguitarplayer on 2009-09-15
hey Iowan, I think our repiles crossed each other,
Synaptic tells me I have Network-Manager installed however I cannot find it.
I have System > Administration > Network Tools and System > Preferences > Network Connections and Network Proxy.
I have looked in System > Preferences > Main Menu and not found it there either.
Is Network-Manager a gui?

---

### Post by Iowan on 2009-09-15
From my (perhaps distorted) perspective, it's an applet. On my system(s), it's located in top right corner near the date/time.  Depending on how I'm connected, it either looks like signal strength bar (wireless) or two monitors (wired).

---

### Post by Iowan on 2009-09-15
I presume you saw [lisati's]("http://ubuntuforums.org/showpost.php?p=7955651&postcount=8") and [my]("http://ubuntuforums.org/showpost.php?p=7955666&postcount=9") replies in the [other]("http://ubuntuforums.org/showthread.php?p=7955651#post7955651") thread?

---

### Post by ozguitarplayer on 2009-09-15
yes I did thanks Iowan thanks, I think I replied in the wrong topic just before.
Being fairly new and unsure about all this I am not sure what to change in /etc/network/interfaces.
I have the two moniters in my panel. I had looked there and it came up as Network Connections not Networking Manager, I didn't realise they are the same thing.
There is MAC addressing there. 
Do I simply fill out Connection Name for each computer and for Mac Address fill in the IP address of each computer.

I don't mean to be slow with this, it's just new to ma and I have found in the past that I can make horrendous mistakes by assuming I kow what I'm doing.

---

### Post by Iowan on 2009-09-16
On Gutsy, it was called Network Connections (although "About" called it **nm-applet**). Seems like static addressing was a bit more complicated in Hardy. I have a few links at home - I'll look them up when I get back later today.

---

