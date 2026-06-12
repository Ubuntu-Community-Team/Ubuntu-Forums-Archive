---
title: "upgrade downloads f/e onto primary b/e"
date: 2011-08-11
forum: Mythbuntu
---

### Post by blkbx on 2011-08-11
Hi
I recently reinstalled mythbuntu 10.04 onto my saparete front and backend machines. Then did a myth-repos upgrade to 0.24x. After configuring the front and backend and settled down to work out the kinks in the setup. Mythbuntu has only worked for me once out of the box(when I replace the localhost to the b/e ip number) All other times it's the usual miss-configs, human error and why the **** won't this work.
So anyway I've done it a few times,  enough to think that I could get it working from my compfy chair and pc and ssh into myth setup instead of trying to drag a monitor into a space way to small for me and it or it and I. Also I'm ok with it, if it does't work on the first day or week. I just want to get it to work and know how I did it. So I took notes. Didn't help! 
Right I get all excited when I get a breakthrough on the pc running the ssh but then wonder why it doesn't work on the front end machine. I realize that it's the backend thats giving me a frontend gui. This is weird because I don't remember downloading it but I check synaptic anyway. Sure enough there it is, Mythtv and mythfrontend. I remove them and viola a working system.
So why would the upgrade do that. Can't they be specific to the role the machine is used for. If not that then could they come with a warning or something. I'm not kicking the guys who make mythbuntu repos availible to the guy on the street but that "is your ip setup correctly" error is a real pain.

---

### Post by williammanda on 2011-08-12
Is it possible to load the latest 11.04 with myth .24? I'm not sure why you are having the issues with 10.04. I upgraded from 10.10 without problem. Why did you pick 10.04? I have two frontends with 10.04 and myth .24 that work fine.

---

### Post by blkbx on 2011-08-12
Hi 
In the end the issue was with the mythbuntu/repos installing mythtv and mythfrontend on my primary backend without me knowing it. I'm only guessing but I probably couldn't get my system(frontend) to work because of a extra config file and or mysql.txt file sitting on the backend machine. I really should have checked, opportunity lost for now I guess. 
As for 11.04 I tried a tonne of times to get it to work and it was probably due to this error that I didn't but really I don't know.
I did have issues trying to install it. My frontend machine is newish so no problem with it but my backend machine has been around the block a few times. I had to buy a graphics card as the onboard gpu wouldn't work with it. I may do an upgrade now that I have things working and have a gig or two left on my plan this month or maybe I'll watch some tv for awhile instead.

---

### Post by nickrout on 2011-08-13
I don't know why your upgrade has dragged in mythtvfrontend, but it doesn't really matter does it? All it does is take up a few M of diskspace. Use apt-get remove to get rid of it if you must.

And yes, you should NEVER use localhost as the ip address of the backend or frontend, it makes it impossible to use a remote frontend and even if you are just starting with a BE/FE combo, you will eventually want to add a frontend and then it is just a hassle to change it.

---

### Post by blkbx on 2011-08-14
Hi 
#toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         In my case having the frontend and mythtv installed did in some way stop my front end machine from connecting, once I removed it everything worked.
    Still hopeing that someone from mythbuntu.org will rread this and give me a litle info as to why the backend upgrade pulleg in mythtv and the frontend.

---

### Post by nickrout on 2011-08-14
please don't post all that crap in your message.

if having a frontend on your backend prevented a remote frontend from connecting it will only be a result of mis configuration on your part.

---

### Post by blkbx on 2011-08-15
Hey man,
I'm really sorry about all crap. I just copied and pasted from abiword. I only have one arm so I tend not to look at the screen alot when I type.
Its possible, I didn't check the f/e config before I removed it.

---

