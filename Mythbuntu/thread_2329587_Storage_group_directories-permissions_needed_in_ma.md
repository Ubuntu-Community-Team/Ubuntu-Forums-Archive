---
title: "Storage group directories-permissions needed in main hard drive?"
date: 2016-07-03
forum: Mythbuntu
---

### Post by jonathan.k3 on 2016-07-03
I'm in the middle of doing a fresh install of mythbuntu 16.04 backend/frontend. I had installed and used 12.04 before with no issues. Did a fresh install because decided to add some hard drives for more recordings. Note: at this point I've just installed mythbuntu and am stuck in the initial setup, haven't mounted the new hard drives yet.

Going through the setup, everything goes smoothly just like before, but I'm stumped by the setup storage directories. I don't remember having to create a directory for the Default group before. But, based on the wiki page: [https://www.mythtv.org/wiki/Setup_Storage_Directories](https://www.mythtv.org/wiki/Setup_Storage_Directories) I put in* */var/lib/mythtv/ but trying to exit the setup gives me a warning message: Unable to create file "/var/lib/mythtv//.test" - directory is not writable?". Don't remember having this issue before.

Do I have to give mythtv read/write permissions in the main hard drive (the one I put the OS on)? If so, how do I do this? Or am I missing something here...

---

### Post by jonathan.k3 on 2016-07-03
Just a quick update, I ended up opening the terminal and used:
sudo chown mythtv: /var/lib/mythtv/

and then
sudo chmod 777 /var/lib/mythtv/

Which seemed to do the trick. Don't know if this was proper but wanted to let others know. If there's a better way, please let me know.

---

### Post by jonathan.k3 on 2016-07-05
So I ended up going to 14.04.4. Everything went well and my system is up and running. Just wanted to note that for Mythbuntu 14.04.4, [COLOR=#000000]/var/lib/mythtv/[/COLOR] is automatically there under the default group in the storage directories during mythtv's backend setup. No need to type it in; also no permissions had to be set up, it just worked. Not sure why this was taken out for Mythbuntu 16.04 and/or mythtv 0.28.

---

### Post by Espryon on 2016-07-06
> **jonathan.k3 said:**
> Just a quick update, I ended up opening the terminal and used:
sudo chown mythtv: /var/lib/mythtv/

and then
sudo chmod 777 /var/lib/mythtv/

Which seemed to do the trick. Don't know if this was proper but wanted to let others know. If there's a better way, please let me know.

You shouldn't need to give read, write, and execute all together to user: group: world. The wiki says default is 755 i.e. user = rwx, group = rx, world = x for the .. and . and chown root:root .. and . and chmod 2775 </insert mythtv subdirectories/> here.
It isn't the best policy to give full permissions and the same goes for giving yourself permanent root access (trust me I know, lol).

Default group access I saw from the wiki would be "Sudo chown mythtv:mythtv </insert mythtv directories i.e. inside mythtv/ here/>

---

