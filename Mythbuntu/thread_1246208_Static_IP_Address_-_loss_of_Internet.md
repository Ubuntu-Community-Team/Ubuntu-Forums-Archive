---
title: "Static IP Address - loss of Internet"
date: 2009-08-21
forum: Mythbuntu
---

### Post by Barry_IA on 2009-08-21
Hi Folks!

Did a search for this problem but was unable to find anything to help.  

When the BackEnd is set for a Static IP address I loose the ability to access the Internet; connects fine with a Dynamic IP Address, but of course the problem is the FrontEnds are unable to find the BackEnd.

The "Wired connection 1" icon at the upper right does not have an 'x', so that's happy.

In previous searches I saw "if it still fails do ifconfig -a and see if udev is seeing this card" -- I don't have a 'udev'.

In the configuration of "Wired connection1" I have:

       Manual (for Static)
       Address    192.168.0.5
       Netmask    255.255.255.0
       Gateway    192.168.0.1           (This will access the DSL Modem on the Windows XP machine and the Mythbuntu machine, the latter whether can connect to the outside world or not.)
       DNS Servers    192.168.0.1
       Search Domains    (is blank)

       The 'Routes" button goes to another set of settings, all of which are blank.  I couldn't find instructions for this so left alone.

Thanks for the assistance!

---

### Post by klc5555 on 2009-08-21
> **Barry_IA said:**
> Hi Folks!

Did a search for this problem but was unable to find anything to help.  

When the BackEnd is set for a Static IP address I loose the ability to access the Internet; connects fine with a Dynamic IP Address, but of course the problem is the FrontEnds are unable to find the BackEnd.

The "Wired connection 1" icon at the upper right does not have an 'x', so that's happy.

In previous searches I saw "if it still fails do ifconfig -a and see if udev is seeing this card" -- I don't have a 'udev'.

In the configuration of "Wired connection1" I have:

       Manual (for Static)
       Address    192.168.0.5
       Netmask    255.255.255.0
       Gateway    192.168.0.1           (This will access the DSL Modem on the Windows XP machine and the Mythbuntu machine, the latter whether can connect to the outside world or not.)
       DNS Servers    192.168.0.1
       Search Domains    (is blank)

       The 'Routes" button goes to another set of settings, all of which are blank.  I couldn't find instructions for this so left alone.

Thanks for the assistance!

So with static IP setup with the backend on 192.168.0.5, the frontends connect to it fine? Just the internet (from the backend)is gone?

Then, first guess and first try: set in 1 or more real DNS server addresses from the outside world when you set the static IP. Don't just use the address of your gateway for the DNS server. See if that does it. (Use DNS servers from your provider's domain. Some providers are reputed to block DNS requests directly to servers outside their own domain).

If not, try 'ping'ing the address of one of these external DNS servers, see if you can actually send packets to the outside world. See whether nslookup can resolve you the address of some outside host on the internet, and whether you can connect to it by the ip address that nslookup has given you. Then maybe we can diagnose from there.

---

### Post by bear24rw on 2009-08-21
when i set up a static ip on my sever i had to set the dns servers to that of my ISP, easy to find check either your router status page or use dhcp to connect and see what it set for dns sever

---

### Post by Barry_IA on 2009-08-22
klc555 and bear24rw:

Thanks to both of you for replying to my inquiry - between both of your answers I figured out the problem, so thankyou-thankyou-THANKYOU!!

What I did was screen printed a couple of pages from the DSL Router -- figured the IP addresses would be there.  Ended up some yes, some no.  (Probably not a bad idea to have this information should something happen to the modem.)

bear24rw suggested the DNS Servers were on the router's Status Page -- hey, lucky me: both of mine are blank! :(    OK, deep breath and set things back for DHCP and copy down those values.  Now set back and hope I don't have to go through a reconfigure.  (Fortunately the machine remembered and everything in the MythTV portion worked.  As a side note for others, I found out if the Recordings are present and work but the Live TV does not and it did before one needs to go to Setup and tab through all five main settings [General, Capture Cards...] and their sub-settings.  Just tab through, using Next or Finish, to 'refresh'.  Be sure the IP address for the BackEnd is correct and the setting for using an individual name for the specific FrontEnd unit are correct.)

Rebooted (for some reason "sudo /etc/init.d/networking restart" doesn't update).  Recordings are there, Live TV works; exit to the Desktop -- Firefox.....?? <holding breath>  YES!!!    <virtual happy dance!>

Now to figure where that second mystery IP address came from in the DHCP settings for the DNS servers -- ah! klc5555's suggestion of 'nslookup'.  That particular command isn't in the book I have so had sort of ignored it at the beginning.  Still not sure but will find out later -- tried nslookup at the beginning but it just sat there with the arrow prompt.  At the end (able to connect to the Internet and the outside world again) tried "nslookup --help".  This time got the arrow prompt, then the 'mysterious' second DNS Server IP Address obtained from resetting to DHCP, then it told me it didn't like the switch command I gave it.  <shrug> I now now how to get the information I need without a lot of switching things back and forth.

So, thanks to both of you.  I appreciate your time.

Barry

---

