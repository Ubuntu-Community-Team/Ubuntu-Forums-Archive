---
title: "XF86AudioPlay through Compiz commands"
date: 2011-10-22
forum: Multimedia Software
---

### Post by nacho-wan on 2011-10-22
Hi there. I have a Samsung  NF210 netbook running Ubuntu 11.04 with unity enabled. Since this little computer doesn't have multimedia keys, I though I could program some shortcuts through xte and compiz command function.

Here is my plan: 
1.use xautomatization to simulate a keypress of XF86AudioPlay. This actually works in terminal: /usr/bin/xte 'key XF86AudioNext'
2.use compiz commands to include a shortcut that will trigger the /usr/bin/xte 'key XF86AudioNext' command.

I didn't have any luck doing the second part. I have tried several key combinations but so far no success. Maybe somebody out there can tell me where I got it wrong?

Thank you!

---

### Post by nm3210 on 2011-10-25
I'm not sure why you're having problems but you sure helped me with mine! 

I have a couple CompizConfig's Commands set to "/usr/bin/xte 'key XF86AudioNext'" (and Prev) and a certain button press on my mouse and it works awesome! But I also could not get the key bindings to work.

You could try just using the Keyboard Shortcuts instead of Compiz, eh?

---

