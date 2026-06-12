---
title: "What IT network questions do I need to ask my boss when ..."
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2010-06-27
Hi I'm thinking about asking my boss at work if I could install Xubuntu on their old public PC where all the hotel guests from different countries uses the PC for simple web surfing.


**Desktop Firewall inexperience**
I'm not experienced with using firewalls on desktops so I'm afraid that when I erase Windows and replaces it with Xubuntu.  I will have made the security layers even lower since I don't know what the previous guy's security knowledge is, and what he has done to protect it.

All I know is that it has Panda firewall on it.  And I don't want my non-IT co-workers having to spend time helping hotel guests when they have firewall access problems.  Since I'm inexperienced in using desktop firewalls with configurations and all that.


**Uncertain about Network connection Settings**
Since I'm not familiar with the company's networking environment.  And there's no IT-manager I can ask directly when at work.  I'm also afraid that when erasing Windows and replacing it with Xubuntu, I won't be able to connect the public hotel PC back to the Internet again.

So what questions do I need to ask my boss and the company's IT-manager via email before I start wrecking things? :p

I have already ran a "cmd--> ipconfig/all" on Windows and written down the ip address and subnet info on paper.  What else do I need to know before the switch?

---

### Post by grahammechanical on 2010-06-27
May I suggest that you set up a dual booting system. Then you can still boot into windows if necessary. Do this until you have ubuntu set up, then hide the boot loader menu so that the computer boots into unbuntu. Or re-install and give ubuntu the whole disc once you have worked out how to set things up.

Also you will need to study the available firewalls for ubuntu. I think that you would want to block off access to certain websites. Especially the .xxx sites that are now allowed to be set up.

Only allow hotel guests to log on in a guest session. That will stop them modifying system settings.

Regards.

---

### Post by jingo811 on 2010-06-27
Thanks grahammechanical, that sounds like a great strategy with a minimum amount of fuss for all involved parties. :)

---

### Post by jonobr on 2010-06-28
Hope you dont mind me sticking my big nose in here.

I just want to add, that you should think of this from your bosses side also,
When you install that and get it running, as far as he is concerned your the expert,
if seomthing goes wrong, your the go to guy,
he will expect you to have all the answers and solutions to problems.
You could imagine your bosses concerns are around security , support, and making sure its less of a pain in the neck to run then windows.
I would recommend spending on security issues such as permissions user controls and iptables.

However, grahammechanical idea is a good backup plan, however, if you rely on that too much , your boss may not be too happy about that.

Cheers and good luck

Jonobr

---

