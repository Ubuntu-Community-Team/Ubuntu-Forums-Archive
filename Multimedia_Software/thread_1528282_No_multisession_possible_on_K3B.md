---
title: "No multisession possible on K3B"
date: 2010-07-10
forum: Multimedia Software
---

### Post by Criminel on 2010-07-10
Hi again,
After upgrading to 10.04 I can no longer burn multisesion discs on K3B.
The multisession option appears before the process of the disc but after the actual burning the discs are no longer appendables.

Does anyone have an idea about this?

---

### Post by AbuHammzah on 2010-07-29
Got the same problem with K3b but Brasero is doing fine..
K3b uses Wodim (from cdrkit) to write multisession discs..
Anyway, I had better results using [cdrtools]("http://cdrecord.berlios.de/") instead of [cdrkit]("http://www.cdrkit.org/").

Here is the ppa for cdrtools:
[https://launchpad.net/~brandonsnider/+archive/cdrtools]("https://launchpad.net/%7Ebrandonsnider/+archive/cdrtools")

add this ppa to your repositories then install cdrecord and mkisofs. (you'll have to remove Wodim and genisoimage)

in the terminal type:
```
sudo add-apt-repository ppa:brandonsnider/cdrtools
sudo apt-get update
sudo apt-get install cdrecord
sudo apt-get install mkisofs
```then when you get the disc ready to burn on k3b, choose cdrecord as the "Writing app".

at least that's how it worked for me...

---

### Post by AbuHammzah on 2010-07-29
Well, just made a multisession dvd with k3b using cdrecord and it failed.. the dvd is complete...

But I'm not givin' up..

I'm not sure what did the trick but here is what I did to make a successful multisession dvd:

[LIST]
[*]Project properties > File system > Custom > (checked the three options on the left especially "Generate UDF structures")
[*]Settings > Configure K3b > Programs > User Parameters > cdrecord > (entered this parameter "-data" without quotation marks)
[/LIST]
I used to burn my discs using BurnAware Free and UDF as a file system and always have a successful multisession dvd.
With a little research I've come to understand that K3b sends the parameter "-xa1" to cdrecord to make a multisession disc which might the problem. The suggested solution presented [here]("http://mandrivausers.org/index.php?act=ST&f=22&t=26077&st=0#entry190847") is to replace this parameter with "-data".

Hopefully useful!

---

