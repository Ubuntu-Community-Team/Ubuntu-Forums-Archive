---
title: "External IP Bash script twitter post"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Bananasdoom on 2010-12-28
I wanted to find my external IP without going to a website so I made this bash script to find your external IP via the terminal or rather through a bash script and then post it on twitter. The first part works but the not the twiter post part, the script is dependent on curl for website scraping and xclip for clipboard copy of IP.

```

#!/bin/bash
# Dependent on curl for website reading and xclip for clipboard copy 
curl www.whatismyip.com/automation/n09230945.asp | xclip -selection c

curl -u username:password -d status=www.whatismyip.com/automation/n09230945.asp https://twitter.com/statuses/update.xml
sleep 10
```

---

### Post by Bananasdoom on 2010-12-28
yes static IP is better but I can deal without it if I have this script, It also makes my Internet bill $10 cheaper to have a dynamic address opposed to static one. I only want to host a small minecraft server for friends and family so there is no need for the extra cost of a static IP.

---

