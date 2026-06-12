---
title: "How to change the MythShutdownCheck script to check for certain application"
date: 2008-09-03
forum: Mythbuntu
---

### Post by bmwman on 2008-09-03
I'm trying to set my MythTV box to shut down by itself and come back on if there is something to record. I'need to edit this script MythShutdownCheck  to check if Azureus or Amarok is running before it shut down. Currently it only checks if other user is currently logged in.

What else do I need to add? Thank you.
Here is the script
```

#
# MythShutdownCheck
#
# checks to see if any other user is
# logged in before idle shutdown
#
# returns "1" if yes, stopping shutdown
# returns "0" if ok to shutdown
#


# to not shutdown during mythcommflag process, uncomment the following line
# ps ax | grep -v grep | grep -q mythcommflag && exit 1


if last | head | grep -q "pts/.*still logged in"   # check for active *remote* login?

then
   exit 1

else
   exit 0
fi
```

---

### Post by bmwman on 2008-09-03
Actually I think I need to edit mythshudown --check script. I'm not sure what's that one checking for.I'm running Azureus overnight to download stuff or use Amarok to listen to music so i need to prevent shut down whenever any of those two are running.

I'm not a developer so I don't really know what is the correct syntax for that but I'm sure it shouldn't be too complicated.

Anyone up for the challenge?
:)

---

