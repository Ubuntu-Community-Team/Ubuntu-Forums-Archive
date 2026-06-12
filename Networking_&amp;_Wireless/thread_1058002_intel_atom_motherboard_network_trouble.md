---
title: "intel atom motherboard network trouble"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by xwaydoublecode1234.rez on 2009-02-02
Hi



I have ubuntu installed on a  intel atom based system


and everything works great. the live cd works great


until


ubuntu downloads updates and asks for a reboot



when the pc is loaded i get a wired connection error


it cant get ip adress through DHCP... but, as i wrote, it works fine with live cd and until updates are installed






what can cause such problems?



when everything goes wrong after updates



thx in advance

---

### Post by paped on 2009-03-23
I have the same issue so any help/advice would be great basically I loaded 8.04.1 server on to the system and it worked fine but after the update(to 8.04.2), 7 to 8 times out of 10 it fails. To double check this I have reloaded 8.04.1 and done the updates again and the same happens.

In addition to the reload I have done the following:
Set the BIOS to optomised defaults - thought this had worked as the system rebooted and got the DHCP address, however after rebooting again the system had the same DHCP issue.
When you use the ipconfig command it shows the Loopback with both an IPv4 and IPv6 address but eth0 just has the IPv6 address (which I think is hard coded in to the card).
If you do a /etc/init.d/networking force-reload the system says send_packet:network unreachable.but before this it sends a DHCPRELEASE to my routers IP which is correct? The system then does 9 lines like this just with different numbers after the interval comment:
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (or 5, 14, 7, 8, 12, 1)
Then says:
No DHCPOFFERS received
No working leases in persistent database - sleeping


Thus any pointers for further testing that I could do or a fix would be appreciated.

---

### Post by kioskgroup on 2009-03-24
I have the same problem! after installing ubuntu 8.10 on my atom pc, everything works great with no known errors. However, after i installed 278 updates, i get no wired connection to the internet, and no local internet access either. I tired setting up a manual connection but no luck either. anyone have any answers?

---

### Post by paped on 2009-03-27
I think I have a workaround for this - well I have rebooted it 10 times done all the updates and the card still works. (touch wood!!!!!)

What I did was change the kernel from the server to the generic one by:
[LIST=1]
[*]Reinstalled server 8.04.1 from cd. Then before doing any updates while the network still worked I did....
[*]I found the current "linux-image" basically the current server kernel by typing "sudo dpkg -l | more" and then scroll down to the linux-image line. Make a note of this line.
[*]Installed the generic kernel by typing "sudo apt-get install linux-image-2.6.xx-xx-generic" (where xx.xx is the same as the currently installed server linux-image you found earlier)
[*]Then remove the server kernel image by typing "sudo apt-get remove linux-image-2.6.xx-xx-server" ---- note: however if there is a newer image it forces you to install it when removing the current one - let the new kernel install then issue the same apt-get remove command with the new xx-xx numbers of the server image that apt has just installed. This will get rid of the server kernel completely just leaving the generic one and stops issues when the kernels are updated.
[*]Reboot using the command "sudo reboot"...... and your nic should still be working when the PC restarts.
[/LIST]

No guarantees - but it worked for me so hopefully it will be helpful to others....

---

