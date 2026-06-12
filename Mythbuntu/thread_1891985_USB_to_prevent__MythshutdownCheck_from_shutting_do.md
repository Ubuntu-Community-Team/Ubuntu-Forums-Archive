---
title: "USB to prevent  MythshutdownCheck from shutting down"
date: 2011-12-07
forum: Mythbuntu
---

### Post by mega30000 on 2011-12-07
Hello,

I am currently using the following MythShutdownCheck script to shutdown if idle on specific days/times.

During long holidays I ssh in and overwrite the VACATION variable with a 1 so that the system doesn't shutdown.

Since the backend is not hooked up to a keyboard or screen but is accessible to my wife and kids I was thinking of having them use a physical key to prevent shutdown.

With a specific USB flash stick inserted during the holidays is there some way to get the script to check for the stick and set VACATION to 1 if the drive was present.  If not it defaults to 0 and the script shuts the computer down.

Any suggestions for how to get the script to recognize if the usb drive is present and return a 1 to the variable.

Thanks

MythShutdownCheck2
#!/bin/sh
# Check generic running time to shutdown
#MythShutdownCheck

DAY=$(date +%u)
HOUR=$(date +%k)
VACATION=1
#this is the variable to allow shutdown to work or not
# a zero funcations as shown, a 1  keeps from shutting down

LOG=/var/log/mythtv/mythbackend.log 
echo "MythShutdownCheck $DAY : $HOUR" >>$LOG 




if last | head | grep -q "pts/.*still logged in"   # check for active *remote* login?

then
        echo "MythShutdownCheck-someone is still logged in" >>$LOG 
   exit 1

else



        if [ $DAY -le 4 ]; then
                if [ $HOUR -ge 23 ] || [ $HOUR -lt 16 ]; then
                        echo "-*-*-*-*-*MythShutdownCheck-*-*-*-*-*" >>$LOG 
                        echo "mon-thur shutdown before 4pm, after 11pm" >>$LOG
                        echo "MythShutdownCheck is ok to shutdown: DAY:$DAY HOUR:$HOUR" >>$LOG 
                        exit $VACATION
                        #
                fi
                exit 1
        elif [ $DAY -eq 5 ] && [ $HOUR -lt 8 ]; then
                echo "-*-*-*-*-*MythShutdownCheck-*-*-*-*-*" >>$LOG 
                echo "MythShutdownCheck: Fri- before 5pm">>$LOG
                echo "MythShutdownCheck is ok to shutdown: DAY:$DAY HOUR:$HOUR" >>$LOG 
                exit $VACATION
                 #
        elif [ $DAY -ge 6 ] && [ $HOUR -ge 2 ] && [ $HOUR -lt 8 ]; then
                echo "-*-*-*-*-*MythShutdownCheck-*-*-*-*-*" >>$LOG 
                echo "MythShutdownCheck: Fri-Sat Night after 2am to before 8am">>$LOG
                echo "MythShutdownCheck is ok to shutdown: DAY:$DAY HOUR:$HOUR" >>$LOG 
                exit $VACATION 
                #should be 0
     elif [ $DAY -ge 7 ] && [ $HOUR -ge 23 ]; then
                #sun after 11
                 echo "-*-*-*-*-*MythShutdownCheck-*-*-*-*-*" >>$LOG 
                 echo "MythShutdownCheck: sun after 11pm" >>$LOG
                echo "MythShutdownCheck is ok to shutdown: DAY:$DAY HOUR:$HOUR" >>$LOG 
                exit $VACATION
                 #should be 0
        else
                exit 1
        fi

exit 0


fi
#end of the check

---

