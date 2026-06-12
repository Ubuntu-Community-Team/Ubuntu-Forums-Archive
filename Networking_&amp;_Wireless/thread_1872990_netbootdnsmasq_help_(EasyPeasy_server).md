---
title: "netboot/dnsmasq help (EasyPeasy server)"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by Vudusu on 2011-10-31
I'm trying to netboot an ancient P3 laptop using an EasyPeasy/Edubuntu netbook, via this guide: [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

The problem is, all the dnsmasq commands,
```
dhcp-range=192.168.1.20,192.168.1.30,12h
enable-tftp
tftp-root=/tftpboot
dhcp-boot=pxelinux.0
dhcp-option=3,192.168.1.1
dhcp-option=4.4.2.1
```

come back "command not found," unless I 
1) prefix them with "dnsmasq" each time, which the guide does not seem to indicate
2) kill dnsmasq between each step.

The commands are accepted using the above steps, but do not result in dnsmasq listening on the desired ports, nor serving the netboot files.

I saw someone with a similar complaint directed to "add the binaries to your path," but I'm a terminal n00b. I have some [general instructions]("http://home.ubalt.edu/abento/linux/terminal/addtopath.html") for adding to path, but no clue what, specifically, I would add for dnsmasq, nor whether it would solve my problem. 

Any advice? Also, any specific distro recommendations for a 1250Mhz PIII w/256MB RAM (Compaq Evo n600)? I got the impression most Ubuntu will run fine on a machine w/ 192MB+, and just grabbed Lucid from the archives. 

Please, no recommendations involving optical or USB media.

---

### Post by bab1 on 2011-10-31
> **Vudusu said:**
> I'm trying to netboot an ancient P3 laptop using an EasyPeasy/Edubuntu netbook, via this guide: [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

The problem is, all the dnsmasq commands,
```
dhcp-range=192.168.1.20,192.168.1.30,12h
enable-tftp
tftp-root=/tftpboot
dhcp-boot=pxelinux.0
dhcp-option=3,192.168.1.1
dhcp-option=4.4.2.1
```

come back "command not found," ...
These aren't terminal commands at all.  You are supposed to add these to the dnsmasq configuration file.  As in:**Append this to /etc/dnsmasq.conf *_with your favorite [text] editor_*: **.

---

### Post by Vudusu on 2011-10-31
](*,) You would not believe how many times I read those instructions and apparently missed that line every time. Thank you for the loan of your eyeballs. 

Though I wish a tutorial aiming to be "complete" would just include the gedit command, rather than gloss over that step out of deference to those with strong feelings about text editors.

---

### Post by bab1 on 2011-10-31
> **Vudusu said:**
> ](*,) You would not believe how many times I read those instructions and apparently missed that line every time. Thank you for the loan of your eyeballs. 

Though I wish a tutorial aiming to be "complete" would just include the gedit command, rather than gloss over that step out of deference to those with strong feelings about text editors.

Glad I could.  I don't think the point was glossed over in the tutorial. 

There is a limit as to how "complete" complete really is.  Sometimes the writer assumes a certain level of expertise from the reader.  In this case the writer assumes that you know how dnsmasq is configured.

In any case I hope it is all working now.

---

### Post by Vudusu on 2011-11-01
The thing is, it's a line to be entered in the terminal, and it was the only line of command omitted from the guide. Moreover, it was almost certainly omitted due to concerns insular to the Linux community and external to the aims of the guide. It was noise in the signal.

I ended up reverse engineering the command from a tutorial on another subject, after doing what any Linux n00b would do first and attempting to navigate to the file via GUI, only to find I couldn't render it writable without the terminal command. I'm pretty sure I did get the netboot set up properly, but the hard drive in the old laptop responded with a sound like brakes that need changing, so I'm thinking this project was strictly a learning experience.

---

### Post by bab1 on 2011-11-01
> **Vudusu said:**
> The thing is, it's a line to be entered in the terminal, and it was the only line of command omitted from the guide. 
You sound like my son when he's avoiding the truth of the situation (e.g. he screwed up).  Not pretty and very obvious.> 
Moreover, it was almost certainly omitted due to concerns insular to the Linux community and external to the aims of the guide. It was noise in the signal.
Insular, you find Linux insular?  I find Linux folk extremely open to new ideas.  You are aware that you have the right to edit the tutorial if you feel you can improve it.  Look in the upper right of the page.  *You *are invited to improve the text.  On the other hand I had no problems understanding the meaning of words like *append *and *editor* > .

I ended up reverse engineering the command from a tutorial on another subject, after doing what any Linux n00b would do first and attempting to navigate to the file via GUI, only to find I couldn't render it writable without the terminal command. 
This is not true.  There are methods to use the GUI to invoke an an editor with the correct privileges.> 

I'm pretty sure I did get the netboot set up properly, but the hard drive in the old laptop responded with a sound like brakes that need changing, so I'm thinking this project was strictly a learning experience.
Maybe for the best.

---

