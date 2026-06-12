---
title: "GLC-Player unavailable?"
date: 2016-05-28
forum: Multimedia Software
---

### Post by Langstracht on 2016-05-28
I recently upgraded to ubuntu 14.04 and have found that I am unable to install GLC-Player.

It worked fabulously well before and I want it again.

Can anyone help?

TIA

---

### Post by ajgreeny on 2016-05-28
I had never heard of it, but here you go!
It is in a get-deb ppa and you can figure out how to get that sorted from [http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/glc-player](http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/glc-player)

---

### Post by Langstracht on 2016-05-28
Thanks for your prompt response.

Based on it I did the following:

```
wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -

sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu xenial-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'

sudo apt-get install glc-player
```

and got the following very disappointing result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package glc-player

You wouldn't happen to know what the problem is would you/

TIA

---

### Post by ajgreeny on 2016-05-28
Before you used the command ```
sudo apt-get install glc-player
``` you must run ```
sudo apt-get update
``` to refresh the repos.

Try that.

---

### Post by Langstracht on 2016-05-28
And it seemed to work:

The following NEW packages will be installed:
  glc-player libglc2
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 1,540 kB of archives.
After this operation, 3,731 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) xenial-getdeb/apps glc-player amd64 2.3.0-1~getdeb1 [861 kB]
Get:2 [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) xenial-getdeb/apps libglc2 amd64 2.2.0-1~getdeb1 [679 kB]

.
.
.

Rebuilding /usr/share/applications/bamf-2.index...
Setting up libglc2 (2.2.0-1~getdeb1) ...
Setting up glc-player (2.3.0-1~getdeb1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...

Alas CLI

```
glc-player
```

results in:

glc-player: command not found

and the Start Center does not find the package ...

---

### Post by mc4man on 2016-05-28
> **Langstracht said:**
> 

```
glc-player
```

results in:

glc-player: command not found

and the Start Center does not find the package ...
the command is glc_player or find in Dash if using unity
Whether a last updated 5 years ago app wil still work without issue would be for you to see..

---

### Post by Langstracht on 2016-05-29
Sorry, hadn't realized that "-" had morphed into "_" ... but then visual acuity was never my strong suit.

Works great and I would recommend it HIGHLY to anyone who needs images of 3D objects ...

---

