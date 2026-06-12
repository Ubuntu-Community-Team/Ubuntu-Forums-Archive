---
title: "Dapper Drake Adsl problem"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by falken on 2006-04-14
my problem is like this...i have a poor phone line and i get disconnected from the phone line 5-6 times a day...because i use my pc remotely i always get stuck on the outisde

so... this is my dial script [www.thewish.host.sk/nix/dial](www.thewish.host.sk/nix/dial) (that connects the modem)

this is the script that should autoreconnect my internet connection when it gets dropped [www.thewish.host.sk/nix/autorecon.sh](www.thewish.host.sk/nix/autorecon.sh)

as a super user i installed a new crontab 

# Every minute (*/1) execute autorecon.sh in your home folder
# redirecting output in /dev/null including errors.
*/1 * * * * /root/autorecon.sh > /dev/null 2>&1

so...when the modem gets disconnected...the script kills the proceses but it doesn't intialize the connect script (/etc/init.d/dial)

this is going on for a week not and it's starting to piss me off

so please help me if you know / can

thanks in advance

---

