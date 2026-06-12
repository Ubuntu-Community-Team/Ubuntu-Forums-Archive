---
title: "Update manager... very slow download!"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by aczar on 2009-03-16
Hello

I installed 8.10 a little while ago and have been trying to run the update manager but for some reason the download speed is always between 100-900 B/s. Very frustrating. Any ideas anyone? 

Thanks

Alex

---

### Post by ugm6hr on 2009-03-17
Perhaps the repository you are using is just busy?

Try a different one, or wait and try some other day.

---

### Post by crazyness003 on 2009-03-17
Well, theare are many factors involved here. Your internet connection speed is the major factor. Since sometimes my ISP throttles ALL of my downloads (sometimes even stalling them completely)
Also, as ugm6hr said, the server you're downloading from may be busy, broken, or overloaded. 
Its always best to take the time to do a speed test and "Select Best Server"

To do this, simply follow these step-by-step instructions. I make downloading fun!

[LIST]
[*] Click the "System" menu
[*] Click the "Administration" sub-menu
[*] Click the "Software Sources" menu-item
[*] Enter your administrator password (or root, sudo, gksu, whatever-password)
[/LIST]
 **ALWAYS BE CAREFUL WHEN YOU DO THIS. **
THIS IS THE ESSENTIAL PART THAT MAKES LINUX INHERENTLY SECURE. MESS AROUND WITH ANYTHING NOW, AND YOU MAY FIND YOURSELF REINSTALLING. SO, ONLY DO THIS IF YOU _ABSOLUTELY_ TRUST WHAT YOU READ. [COLOR=Red]AND ALWAYS READ AHEAD BEFORE DOING ANYTHING!!![/COLOR]
If you don't trust me, or if anyone is suspicious of this, this post will most likely be deleted. So, you decide.
[INDENT]After your password is successfully entered, you will be greeted by a window. Midway down the window, you'll see a label "Download from:" followed by a combobox. 
[/INDENT]
[LIST]
[*] Click combobox
[*] Click "Other..." option
[/LIST]
[INDENT] You will be greeted by another window. On the right, you will see a button "_S_elect Best Server"
[/INDENT]
[LIST]
[*] Click button
[/LIST]
[INDENT] It will test almost all servers containing Ubuntu repositories and pick the fastest one. This selection might change if you do it again, due to many other factors (time of day, location, etc).

After its done testing, and selecting a server for you...
[/INDENT]
[LIST]
[*] Click "Choose _S_erver"
[/LIST]
[INDENT] The window will close
[/INDENT]
[LIST]
[*] Click "**[COLOR=Red]X[/COLOR]** _C_lose" on the next window
[/LIST]
[INDENT] It will prompt you with a dialog. IT basically says you have to update your package info.
[/INDENT]
[LIST]
[*] Click "[COLOR=Lime]O[/COLOR] _R_eload"
[/LIST]
[INDENT] This will download new package information, so next time you run an update, download from apt/aptitude/synaptic, or whatever, it will be in sync with the server it picked for you earlier, meaning it will *probably* be faster than before.
[/INDENT] There. I hope this helps at least 1 person. Since this is my 400th post.
Have fun

---

### Post by nelskurian on 2009-03-17
If you are in a local network with lots of ubuntu machines,you can try **apt-proxy** or simply use other machines repository cache as local repository.

---

### Post by crazyness003 on 2009-03-17
> **nelskurian said:**
> If you are in a local network with lots of ubuntu machines,you can try **apt-proxy** or simply use other machines repository cache as local repository.
wow. I didn't know that. So, essentially, instead of updating all of your machiens from the internet, you can just update 1, then update the rest off of that one? Cool. That would be OVER9000 times faster.

---

### Post by nelskurian on 2009-03-17
> wow. I didn't know that. So, essentially, instead of updating all of your machiens from the internet, you can just update 1, then update the rest off of that one? Cool. That would be OVER9000 times faster.
Ya surely..You can put one machine as the apt-proxy server and needs to update that machine only.Also even if one of the network machine updates a package,It also comes through the apt-proxy and the proxy cache updated with that package.
   For that you need to configure the sources.list in each PC's for using the apt-proxy server.

You can find more abt apt-proxy configuration from below.
[https://help.ubuntu.com/community/AptProxy]("https://help.ubuntu.com/community/AptProxy")

---

### Post by crazyness003 on 2009-03-17
> **nelskurian said:**
> Ya surely..You can put one machine as the apt-proxy server and needs to update that machine only.Also even if one of the network machine updates a package,It also comes through the apt-proxy and the proxy cache updated with that package.
   For that you need to configure the sources.list in each PC's for using the apt-proxy server.

You can find more abt apt-proxy configuration from below.
[https://help.ubuntu.com/community/AptProxy]("https://help.ubuntu.com/community/AptProxy")
1 cookie for you. I'd thank you, but I cant.

---

### Post by aczar on 2009-03-17
I thought it may be a busy server a little while ago as well, but I've been trying on and off for several weeks and it's always the same. I'll give finding a faster server a shot none the less.

---

### Post by aczar on 2009-03-17
> **nelskurian said:**
> Ya surely..You can put one machine as the apt-proxy server and needs to update that machine only.Also even if one of the network machine updates a package,It also comes through the apt-proxy and the proxy cache updated with that package.
   For that you need to configure the sources.list in each PC's for using the apt-proxy server.

You can find more abt apt-proxy configuration from below.
[https://help.ubuntu.com/community/AptProxy]("https://help.ubuntu.com/community/AptProxy")

Don't have any other ubuntu machines on the network, but I'll keep this in mind for the future. Thanks!

---

### Post by crazyness003 on 2009-03-17
> **aczar said:**
> I thought it may be a busy server a little while ago as well, but I've been trying on and off for several weeks and it's always the same. I'll give finding a faster server a shot none the less.
dont rule out the fact that your personal internet connection may suck. Im not trying to be mean or anything, but try running internet connection tests to gauge your connection speed (not the broadband speed, actual internet speed. You can do that [here]("http://www.auditmypc.com/internet-speed-test.asp"))

This is my stats (in the attachments), But I have the fastest connection my ISP provides for home use (and its not cheap)
Also, its noon, so there isn't much load on the ISP bandwidth. The later it gets, the slower, due to everyone logging in and using up resources.

---

### Post by aczar on 2009-03-17
> **crazyness003 said:**
> dont rule out the fact that your personal internet connection may suck. Im not trying to be mean or anything, but try running internet connection tests to gauge your connection speed (not the broadband speed, actual internet speed. You can do that [here]("http://www.auditmypc.com/internet-speed-test.asp"))

This is my stats (in the attachments), But I have the fastest connection my ISP provides for home use (and its not cheap)
Also, its noon, so there isn't much load on the ISP bandwidth. The later it gets, the slower, due to everyone logging in and using up resources.

haha... no offence taken. No, it's a decent connection. I also have the fastest connection my ISP provides for home use (and it is also not cheap :()

I've tried the updates at all times of day and night. I haven't tried speed tests on ubuntu, but I've done them with windows on the same machine.

---

### Post by aczar on 2009-03-17
It worked! Thanks a lot crazyness.... I guess I was just connected to a really slow server. 
Many thanks to all those who offered suggestions

---

### Post by crazyness003 on 2009-03-18
> **aczar said:**
> It worked! Thanks a lot crazyness.... I guess I was just connected to a really slow server. 
Many thanks to all those who offered suggestions
\\:D/ Make sure you mark this thread as solved.
And you're welcome.

---

### Post by Dalif on 2009-04-24
Just wanted to chime in and thank crazyness. This solved my problem as well. One google search, one forum post. Problem solved. Thanks!

---

### Post by crazyness003 on 2009-04-26
Shwiggimus-prime! Glad I could help.

---

### Post by kpothi on 2009-10-03
Thanks for those who posted the replies. I'm currently using "Update Manager" with a speed of 1/1000 of usual speed. I assume it's probably due the slow server. Thanks again for your answers.

---

### Post by KeithE4 on 2009-10-03
> **kpothi said:**
> Thanks for those who posted the replies. I'm currently using "Update Manager" with a speed of 1/1000 of usual speed. I assume it's probably due the slow server. Thanks again for your answers.

I've been having the same problem for the last few days, since Sept. 30, 2009.  Everything else on the web, including downloads from other sites, is fast.  Ubuntu updates are at dialup speed.

---

### Post by emeraldgirl08 on 2009-10-04
I thank you guys for posting this!

I know for sure I don't have dial-up anymore but I've had to reinstall Jaunty on one of my laptops and the updates have been pissing me off!

I'll try this on one of my other machines soon!

---

