---
title: "Wired eth0 network + wireless internet connect = no mailx"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by bmckinley on 2012-03-01
Recently moved and current setup has internet connection via wifi router.  Also have local network setup (3 boxes) on eth0.  I have configured the local network connections to use routes only for resources on local, which allows the wifi to connect to internet.

So far so good, except I have several monitoring scripts that use command line mail/mailx to send alerts if there is a problem, and with this network configuration, the alerts are not being sent. The scripts are verified and working and as a test I have tried to use:
cat transfer_log | mail -s "Transfer log results for $(date '+%F')" [EMAIL="my_email@server.com"]my_email@server.com[/EMAIL]

No success.

Can anyone suggest a correct configuration for this to work?  It seems that the mail function wants to use the eth0 connection and needs to instead use the wifi connection.  Because of the physical setup in the rental house, there is not an option other than wifi for internet connect.

Thanks for any help.

---

