---
title: "Network bypass"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by tadashi on 2006-02-21
Is there a parameter to tell Kubuntu not to load network stuff?  Normally, I work at home and have a WiFi connection but if I try to boot the system anywhere else my boot up hangs for a couple minutes until the network times out.

---

### Post by Lambert on 2006-02-21
If you open up the file /etc/network/interfaces (with sudo or root privledges) you will see something like this.

auto eth0

remove the auto interface line from any interface you don't want to start at boot. Leave the auto lo one there as it's important for network to work properly.

---

### Post by tadashi on 2006-02-21
There is not a way to do it wat the grub boot menu like a kernel boot parameter?  This way I can either have a menu item to select depending if I open the laptop at home or work.

---

### Post by Lambert on 2006-02-21
Here is what happens currently on boot.

When the networking script is run at boot, it runs a command *ifup -a *This looks for any interface with the auto stanza and trys to bring up and configure that interface.

You can remove these auto stanzas as I suggested and it won't configure anything at boot.

Now as far as a chooser during boot, I know of nothing. But there are scripts floating around this forum which you can add to run at start which basically searches for known ap's you've set in the script and connects to the recognized ap.

I can't help you with this as it's outside of my knowledge. You can search the forum to find it, I believe it's here in the networking section.

You can also look [here  ]("http://doc.gwos.org/index.php/WLAN_Autodetect")to see if this offers anything.

---

### Post by tadashi on 2006-02-21
What if I take the auto line out and have script files like in [http://news.com.com/2102-1002_3-6028275.html?tag=st.util.print](http://news.com.com/2102-1002_3-6028275.html?tag=st.util.print) ? Then I can boot without the waiting for timeout and just run the appropriate script file if I want to connect?

---

### Post by Lambert on 2006-02-21
running a script works. You can create a launcher on a panel or on the desktop so when you click it runs the script. You could create a simple script for each ap you connect to and a separate launcher.

I'm not that good at it but now that I think about it, you could run a script that prompts you for a choice and then runs your choice. Can't help you here but could be a great learning experience to play around with all the options.

It's the best part I find in Linux, there are many ways you can do this, find one that works for you. You have the freedom to customize the os to your taste. :-D

---

### Post by tadashi on 2006-02-21
Cool, thanks.  I will have to look into prompting scripts.

---

