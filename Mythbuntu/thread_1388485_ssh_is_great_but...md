---
title: "ssh is great but.."
date: 2010-01-23
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-01-23
I have setup my mythbox to accept ssh connections for remote admin and its great but is there any remote admin that allows a graphical interface?  The terminal is great for most things but as im fairly new to to linux (only a few years in) i still find somethings easier with a gui (creating symblinks etc).

Thanks

---

### Post by d3v1150m471c on 2010-01-23
I'd be careful with that. You start giving applications ssh capabilities and that's when your backtrack script kiddies and the iron curtain ip trollers start bruteforcing your system and turn your operating system into mush or a zombie.

If you want your torrent client to activate while you're away then leave your system on and learn how to use crontab.

---

### Post by geekyhawkes on 2010-01-23
you saying i should be careful with ssh or any kind of graphical remote admin?  I had thought ssh was fairly secure?

---

### Post by d3v1150m471c on 2010-01-23
ssh is secure until someone runs a bruteforcer on it. Depending on the bruteforcer and your password, this could take anywhere from a matter of minutes to a few hours. Longer and character laden passwords are your friend. 

[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/](http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/)

[http://www.youtube.com/watch?v=6Oh3rR35Tgs](http://www.youtube.com/watch?v=6Oh3rR35Tgs)

watch/read both of those...especially the youtube video. that's how retarded easy it is to crack ssh.

^^^ 4 minutes and system compromised. cover your 6, mate.

---

### Post by geekyhawkes on 2010-01-23
Thanks, guess the best way is to only enable ssh when i really need it!

---

### Post by d3v1150m471c on 2010-01-23
no problem brother. not trying to beat a dead horse but if you didn't already check out that first link. I've tested it and it works wonders. That link also comes with a great crontab howto if you're not familiar with it.

---

### Post by geekyhawkes on 2010-01-23
Motion sickness youtube video!  But does make the point i guess.

---

### Post by llawwehttam on 2010-01-23
> **geekyhawkes said:**
> Motion sickness youtube video!  But does make the point i guess.

That youtube video was rubbish. He was hacking a local server with a dictionary word password. As long as u have a reasonable password ( at least 7 characters non dictionary) then you should be alright. 

Lol my computer has a 32 character password.

---

### Post by d3v1150m471c on 2010-01-23
Most brute forcers, serious ones anyways, aren't going to rely on crap dictionary passwords. They'll run through every possible key combination and length until they hit the jackpot. It's a matter of time rather than a yes or no it won't happen.

---

### Post by geekyhawkes on 2010-01-23
i had kind of not really thought that much about how exposed my myth box might have been.  SSH is off for now and i will only put it on when i actually need to remote admin, i have also switched off vnc as well (thinking along the same lines).  I have a decent password for mythweb so not too concerned about leaving that exposed. 

Thanks for the steer.

---

### Post by desktopj on 2010-01-23
> **geekyhawkes said:**
> i had kind of not really thought that much about how exposed my myth box might have been.  SSH is off for now and i will only put it on when i actually need to remote admin, i have also switched off vnc as well (thinking along the same lines).  I have a decent password for mythweb so not too concerned about leaving that exposed. 

Thanks for the steer.

I disagree. I've used openssh for ten years to administrate servers and networks remotely without having a single successful external attack. 

1. Disable ssh passwords and use keys [http://ubuntuforums.org/archive/index.php/t-30709.html]("http://ubuntuforums.org/archive/index.php/t-30709.html")
2. Use ssh tunnels to access any network protocols behind your firewall. I use Putty as a ssh client a lot, makes tunnels easy and is available on any OS I use. You can leave Vnc, http or whatever left on and open since it's not exposed outside your network.

I'm paranoid (my clients security is at stake), so I also create a low privileged ssh user (and the only ssh user) with a user name that looks something like user=rtwss33ytra54 and use su/sudo to become any user. I also move my ssh port to some high number like 56774 just to keep the script kiddies discouraged.

SSH is great, period. Then use vnc, x11 or console securely on your network.

Jeff

---

### Post by movieman on 2010-01-23
Indeed. If you want to perform remote admin with GUI tools, then leave VNC running configured for localhost access only so it can't be hacked from outside, configure ssh to use a non-standard port, and either disable password logins or use a long, randomly-generated password. Then you can use port-forwarding on SSH to forward the VNC port on the server to the VNC port on the local machine, and connect to it with a VNC viewer.

I forget the details, but the commands are something like:

vncserver --localhost ( on the server )
ssh -L localhost:5901:localhost:5901 user@server (on the remote)

If you're only using it for port-forwarding, then you can probably configure ssh to only allow logins by a specific low-privilege user and configure that user to not run a shell after logging in.

---

### Post by azmyth on 2010-01-23
Just use something like FreeNx or the actual Nxclient. The later can be found at nomachine.com. If you're really worried about attacks, then you can turn on key based auth for ssh. Nxclient works with key auth whereas I couldn't get FreeNX to work. It's kind of a pain to setup but once you get it going it's a piece of cake.

---

### Post by movieman on 2010-01-23
True, I've been meaning to try the FreeNX interface instead of VNC.

---

### Post by geekyhawkes on 2010-01-23
how do I change the ssh port in myth? I was also thinking of setting port forwarding on my router getting round the port 22 problem. I like movie man's ssh port forward idea to vnc, I'm just having a dull moment in my head fully understanding it. I've been using pocket putty on my hd2 and have been pretty pleased with it.

---

### Post by movieman on 2010-01-23
I think all the ssh configuration is in /etc/ssh/sshd_config.

---

### Post by geekyhawkes on 2010-01-23
Thanks i will give it a look and see how i get on.  I guess its all too easy to click a tick box and not really think about the implications, its certainly the trap i fell into even though i REALLY should have known better.

---

### Post by johnvan on 2010-01-23
It's easier to have your router redirect a port externally to the standard listening port 22.
I use a high 5 digit port which my router redirects. I disable SSH password login in my router (PFsense) and use a key pair. Any router should have these abilities, personally I find it simpler because it's a nice GUI.
For a quick way to open a tunnel to your desktop try GSTM.

---

### Post by nickrout on 2010-01-23
how are you going to turn on ssh once you have turned it off?


however you shouldn't have your mythbox exposed to the internet anyway. It should be firewalled.

if you are silly enough to expose it to the internet, if you want to avoid dictionary attacks install denyhosts. More than a set number of login attempts will lock out the IP address the attack is coming from.

Also you should turn off password authentication and use key authentication.

---

### Post by 2hot6ft2 on 2010-01-25
I set up ssh and freenx yesterday and they'll never get in that way.
Anyone setting up ssh and freenx should start here [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Follow links, read and compare setting them up instructions

Definitely change the port to something other than the default 22
But they left out setting up the clients ssh files port
Both host and client files will need to be changed so edit both to the same port # along with the hosts firewall.

sshd_config is the configuration file for the OpenSSH server (/etc/ssh/sshd_config).
ssh_config is the configuration file for the OpenSSH client (/etc/ssh/ssh_config).
Make sure not to get them mixed up.

and
> SSH can use either "RSA" (Rivest-Shamir-Adleman) or "DSA" ("Digital Signature Algorithm") keys. Both of these were considered state-of-the-art algorithms when SSH was invented, but DSA has come to be seen as less secure in recent years. RSA is the only recommended choice for new keys, so this guide uses "RSA key" and "SSH key" interchangeably.
from here [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

> Key Encryption Level

Note: The default is a 2048 bit key. You can increase this to 4096 bits with the -b flag (Increasing the bits makes it harder to crack the key by brute force methods).

ssh-keygen -t rsa -b 4096

When setting up FreeNX use custom keys not the default keys when prompted.

and
> Disable Password Authentication

Because a lot of people with SSH servers use weak passwords, many online attackers will look for an SSH server, then start guessing passwords at random. An attacker can try thousands of passwords in an hour, and guess even the strongest password given enough time. The recommended solution is to use SSH keys instead of passwords. To be as hard to guess as a normal SSH key, a password have to contain 634 random letters and numbers. If you'll always be able to log in to your computer with an SSH key, you should disable password authentication altogether.

If you disable password authentication, it will only be possible to connect from computers you have specifically approved. This massively improves your security, but makes it impossible for you to connect to your own computer from a friend's PC without pre-approving the PC, or from your own laptop when you accidentally delete your key.

It's recommended to disable password authentication unless you have a specific reason not to.

To disable password authentication, look for the following line in your sshd_config file:

#PasswordAuthentication yes

replace it with a line that looks like this:

PasswordAuthentication no

Once you have saved the file and restarted your SSH server, you shouldn't even be asked for a password when you log in.  


That in itself will make that dictionary attack useless.

Once it's all set up it's great complete with GUI.
:popcorn:

> **nickrout said:**
> how are you going to turn on ssh once you have turned it off?


however you shouldn't have your mythbox exposed to the internet anyway. It should be firewalled.

if you are silly enough to expose it to the internet, if you want to avoid dictionary attacks install denyhosts. More than a set number of login attempts will lock out the IP address the attack is coming from.

Also you should turn off password authentication and use key authentication.
To turn off ssh use
```
sudo /etc/init.d/ssh stop
```

---

### Post by dougsnell on 2010-01-25
> **geekyhawkes said:**
> I have setup my mythbox to accept ssh connections for remote admin and its great but is there any remote admin that allows a graphical interface?  The terminal is great for most things but as im fairly new to to linux (only a few years in) i still find somethings easier with a gui (creating symblinks etc).

Thanks

OK, maybe I'm missing something here, but does your box have a publicly accessible IP?  My guess is you don't; like most people you probably have myth on your home router/network.

[http://www.grc.com/nat/nat.htm](http://www.grc.com/nat/nat.htm)

Hopefully you have *some* level of security on your router, and sit behind it.  About your only vulnerability that jumps to mind is if you leave your wireless router unsecured.

If you're behind a router, turn on SSH and VNC, and go nuts.  FWIW, I've found that learning the SSH commands is typically beneficial, but ... that's me.

---

### Post by geekyhawkes on 2010-01-26
My myth box is on my home router and there is a firewall involved as well.  There are loads of good tips here on generally securing exposed systems so i will probably just work through setting up ssh for key based log ons and not just password.  That seems a "good enough" solution for me i think.  I will move the ssh port from 22, and to be honest i think i can just do that with some port forwarding via the router and leave myth at the default settings.

I think there is definatly some good advice here for anyone wanting to understand what they are exposing.

---

### Post by SiHa on 2010-01-27
dougsnell does make a good point though.
My network is behind a router. On all four machines, I've looked at a week's worth of auth.log's and there is not a single authorisation attempt that isn't mine.
That said key-based ssh makes sense, if for no other reason than not having to type a password each time!

---

### Post by geekyhawkes on 2010-01-27
I guess while we are talking about this, how secure is it to have mythweb "exposed"?  I guess using port forwarding away from the default of http (80 from memory) might be an idea?

---

### Post by nickrout on 2010-01-27
It is not secure at all. If you do it make sure it is password protected. Ideally do it via ssh tunelling. There are plenty of howtos on the net.

Changing ports adds no security. Crackers try all your ports. Its a red herring at most.

---

### Post by geekyhawkes on 2010-01-28
It is password protected, but how secure is the apache server that myth uses?  Everything has problems and ssh tunneling isnt really an option as i often use my hd2 to get access to myth web and not sure ssh tunneling would work via windows mobile.

---

### Post by DZ* on 2010-01-28
> **d3v1150m471c said:**
> Most brute forcers, serious ones anyways, aren't going to rely on crap dictionary passwords. They'll run through every possible key combination and length until they hit the jackpot. It's a matter of time rather than a yes or no it won't happen.

But it might be a matter of some *very long* time. Even if passwords are composed of only letters and numbers, an eight character password is one of (26*2 + 10)^8 = 2.183401e+14 combinations. 

To increment a 64 bit integer to that value within a compiled program would take a week on an average PC. How much slower is a single communication with sshd compared to a single 'long long int' operation?

---

