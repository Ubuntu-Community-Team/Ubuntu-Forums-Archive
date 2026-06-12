---
title: "PPPoE problems answered (finally)"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by imrumpf on 2005-12-30
Ok please do not get mad at me for creating a new post. I have seen many threads asking for help on what to do to get a DSL modem working. I spend a good 3 hours reading them and none helped at all. But I stumbled upon a fix that I would like to share. Please feel free to comment on it and suggest alternatives/fixes/etc.

For the DSL modem I was setting up, the only way to get everything working was to run the following command in the terminal EVERY TIME i wanted to connect:

```
sudo pppoeconf
``` 
Then some threads suggested that I add "pon dsl-provider" to the Startup programs under sessions. No good, and had to run pppoeconf all over again just to connect.

**Here is my fix:**[LIST=1]
[*]use "sudo pppoeconf" and configure the connection.
[*]make sure you have a working internet connection.
[*]System --> Administration --> Synaptic Package Manager
[*]Settings --> Repositories
[*]Settings --> Show Disabled Software sources
[*]close it all down
[*]Terminal
[*]```
sudo apt-get update
```
[*]```
sudo apt-get install pppoe
```
[*]It **should** ask to replace the dsl-provider file (at least that's what happened with me) Choose **yes**
[*]```
sudo gedit /etc/ppp/peers/dsl-provider
```
[*]Replace:```
# MUST CHANGE: Uncomment the following line, replacing the user@provider.net
# by the DSL user name given to your by your DSL provider.
# (There should be a matching entry in /etc/ppp/pap-secrets with the password.)
#user myusername@myprovider.net
``` with ```
# MUST CHANGE: Uncomment the following line, replacing the user@provider.net
# by the DSL user name given to your by your DSL provider.
# (There should be a matching entry in /etc/ppp/pap-secrets with the password.)
user **b1********
``` **NOTE: **The b1****** is an example of a sympatico username, change it to what you need.
[*]Save/exit
[*]System --> Preferences --> Sessions
[*]Startup programs --> Add
[*]Add these two entries:```
pon dsl-provider
``````
dsl-provider
``` Sorry for the two entries, I was trying ANYTHING to get it to work and that just worked. I didn't have time to check to see which one did the trick so I left both.[/LIST]And there you have it! Restart the computer and you should automatically have your DSL connection running when you log in. It worked for me, how does it work for any other people?

Again I am sorry if it was obvious for some of you but I'm happy I did most of this on my own :razz:

---

### Post by Kishandr on 2006-10-20
i tired this but i am uable to configure my sympatico connection .i get erro etc/ppp/peer/dsl-provider unrecongnised 'nic-ath0' .How to configure the for pap authentication as sympatico uses pap authentication.I am new to linux so please give me compelete details.

---

### Post by imrumpf on 2006-10-20
can you please provide the information contained in the file so I can see what's going ok? thanks.

---

