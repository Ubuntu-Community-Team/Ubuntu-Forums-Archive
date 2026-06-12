---
title: "frontend telnet conkyrc addon script"
date: 2009-04-12
forum: Mythbuntu
---

### Post by oobe-feisty on 2009-04-12
i recently discovered this as i had a need for somthing else but i thought it might be nice to check the status of remote and local frontends [http://www.mythtv.org/wiki/Telnet_socket](http://www.mythtv.org/wiki/Telnet_socket)

i wrote a script that displays local and remote frontends status in conky i would like to share it with you im just learning about scripting and this is my first attempt at variables i mostly just put stuff in that i could be typed type from shell with no variables or error correction so i learned a bit preparing this.

attached are screenshots the instructions on how to use are in the comments of the file and the above link should let you know about mythtv telnet and how to enable it can be found [here]("http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#General_.28page_4.29")

```

#!/bin/bash
#Made By Kemble Wagner
#To use this Script you need to Enable Network Remote Control Interface on Mythfrontend
#Thanks to wagnerrp from mythtv-users on freenode for his contributions and tips
#the output files are meant to be used with conky
#e.g .conkyrc
#${color #8844ee}Local Frontend Status:
#${color #8844ee} ${execi 30 mythnc.sh > /dev/null && cat /var/tmp/local.myth}
#${color #8844ee}Remote Frontend Status:
#${color #8844ee} ${execi 30 mythnc.sh > /dev/null && cat /var/tmp/remote.myth}
#Version 0.2 14/04/09  
#Version 0.3 "       " fixed sed to make it parse long file names and unusual characters with spaces and no spaces when outputting Video Playback
#Version 0.4 "       " added more events to output in human friendly terms changes it so only one instance of nc is used to prevent hammering of ports
#Version 0.5 17/04/09 add some fixes to playback status and added a check status in the even the frontend not running but the host is up



#change the host names to suit add more if needed
LOCALHOST=box
#path to text file leave as default is ok 
OUTPUTFILE1=/var/tmp/local.myth
OUTPUTFILETMP1=/var/tmp/local.myth.tmp
FETEST1=/var/tmp/local.fetest
FILENAME1=`cat $OUTPUTFILETMP1 | grep 'Playback Video' |sed  -e 's/[[ \t]]*/_/g' | sed 's/\(.*\)\..*/\1/' |  sed  's/  *//g' | sed -e 's/^.*\///;s/ .*$//'`
RECFILE1=`cat $OUTPUTFILETMP1 | grep 'Playback Recorded' |sed  -e 's/[[ \t]]*/_/g' | sed 's/\(.*\)\..*/\1/' |  sed  's/  *//g' | sed -e 's/^.*\///;s/ .*$//'`
#remote host variables


#the stuff below is an attempt to convert telnet status info into human friendly readable info

#below are localhost checks

nc -c exit  $LOCALHOST 6546 && echo opened >  $FETEST1|| echo closed > $FETEST1


#Checking if MythFrontend is running 


if (cat $FETEST1 | grep closed ); then
  echo "$LOCALHOST is up but MythFrontend doesn't seem to be running" > $OUTPUTFILE1 

else
echo -e "query location\nexit" | nc $LOCALHOST 6546 > $OUTPUTFILETMP1
fi

#Checking for TV recording Menu
if (cat $OUTPUTFILETMP1 | grep PlaybackBox ); then
  echo "$LOCALHOST is Idle in TV Recordings Menu" > $OUTPUTFILE1

else 

#Checking for Program Guide
if (cat $OUTPUTFILETMP1 | grep GuideGrid ); then
  echo " $LOCALHOST is in TV Guide" > $OUTPUTFILE1
else 

#Checking for MythVideo Gallery
if (cat $OUTPUTFILETMP1 | grep videogallery ); then
  echo "MythVideo Menu On $LOCALHOST is Idle" > $OUTPUTFILE1
else 

#Checking for MythVideo Listings
if (cat $OUTPUTFILETMP1 | grep videolistings); then
  echo "MythVideo Menu On $LOCALHOST is Idle" > $OUTPUTFILE1
else 

#Checking for MythVideo Browser
if (cat $OUTPUTFILETMP1 | grep videobrowser); then
  echo "MythVideo Menu On $LOCALHOST is Idle" > $OUTPUTFILE1
else 
#Checking for MythMusics
if (cat $OUTPUTFILETMP1 | grep playmusic ); then
  echo "Playing Music Cant you Hear?" > $OUTPUTFILE1
else 

#Checking for MainMenu
if (cat $OUTPUTFILETMP1 | grep MainMenu ); then
  echo "$LOCALHOST is in The Main Menu" > $OUTPUTFILE1

else 

#Checking for Live TV
if (cat $OUTPUTFILETMP1 | grep "Playback LiveTV" ); then
  echo "$LOCALHOST is Watching Live TV" > $OUTPUTFILE1
else 

#Checking for MythVideo Playback
if (cat $OUTPUTFILETMP1 | grep "Playback Video" ); then
  echo "MythVideo is playing $FILENAME1" > $OUTPUTFILE1
else 
 
if (cat $OUTPUTFILETMP1 | grep  "Playback Recorded" ); then
    echo "MythTV is playing recording $RECFILE1" > $OUTPUTFILE1
else





#if none of the above simply display then query status output
if (cat $OUTPUTFILETMP1 | grep "#"); then 
cat   $OUTPUTFILETMP1 | grep "#" > $OUTPUTFILE1 


fi 
  fi 
     fi 
        fi   
           fi
              fi 
                fi
                  fi
                     fi
                        fi
                          fi
                            
                        


#setting remote host variables you can reproduce this for as many hosts as you want
REMOTE=frontend
OUTPUTFILE2=/var/tmp/remote.myth
OUTPUTFILETMP2=/var/tmp/remote.myth.tmp
# script gets slow if the host is not up when continueing to set remote host variables so check its up first
#checking remote frontend is up first
if ! `/bin/ping -W1 -c1 $REMOTE >/dev/null 2>&1` ; then
echo "$REMOTE Seems Offline" > $OUTPUTFILE2 && exit 0
else

#contine setting remote host variables 

FILENAME2=`cat $OUTPUTFILETMP2 | grep 'Playback Video' |sed  -e 's/[[ \t]]*/_/g' | sed 's/\(.*\)\..*/\1/' |  sed  's/  *//g' | sed -e 's/^.*\///;s/ .*$//'`
RECFILE2=`cat $OUTPUTFILETMP2 | grep 'Playback Recorded' | sed -e 's/^.*\///;s/ .*$//' | sed 's/\(.*\)\..*/\1/'`
FETEST2=/var/tmp/remote.fetest


#below are remote host checks

nc -c exit $REMOTE 6546 && echo opened >  $FETEST2|| echo closed > $FETEST2

#Checking if MythFrontend is running 

if (cat $FETEST2 | grep closed ); then
  echo "$REMOTE is up but MythFrontend doesn't seem to be running" > $OUTPUTFILE2 

else

echo -e "query location\nexit" | nc $REMOTE 6546 > $OUTPUTFILETMP2
fi


#Checking for TV recording Menu
if (cat $OUTPUTFILETMP2 | grep PlaybackBox ); then
  echo "$REMOTE is Idle in TV Recordings Menu" > $OUTPUTFILE2 
else 

#Checking for Program Guide
if (cat $OUTPUTFILETMP2 | grep GuideGrid ); then
  echo "$REMOTE is in TV Guide" > $OUTPUTFILE2
else 

#Checking for MythVideo Gallery
if (cat $OUTPUTFILETMP2 | grep videogallery ); then
  echo "MythVideo Menu On $REMOTE is Idle" > $OUTPUTFILE2
else 

#Checking for MythVideo Listings
if (cat $OUTPUTFILETMP2 | grep videolistings); then
  echo "MythVideo Menu On $REMOTE is Idle" > $OUTPUTFILE2
else 

#Checking for MythVideo Browser
if (cat $OUTPUTFILETMP2 | grep videobrowser); then
  echo "MythVideo Menu On $REMOTE is Idle" > $OUTPUTFILE2
else 

#Checking for MythMusics
if (cat $OUTPUTFILETMP2 | grep playmusic ); then
  echo "Playing Music Cant you Hear?" > $OUTPUTFILE2
else 

#Checking for MainMenu
if (cat $OUTPUTFILETMP2 | grep MainMenu ); then
  echo "$REMOTE is in The Main Menu" > $OUTPUTFILE2
else 

#Checking for Live TV
if (cat $OUTPUTFILETMP2 | grep "Playback LiveTV" ); then
  echo "$REMOTE is Watching Live TV" > $OUTPUTFILE2
else 

#Checking for MythVideo Playback
if (cat $OUTPUTFILETMP2 | grep "Playback Video" ); then
  echo "MythVideo On $REMOTE is playing $FILENAME2" > $OUTPUTFILE2
else 
 
if (cat $OUTPUTFILETMP2 | grep  "Playback Recorded" ); then
    echo "MythTV On $REMOTE is playing recording $RECFILE2" > $OUTPUTFILE2
else



#if none of the above simply display then query status output
if (cat $OUTPUTFILETMP2 | grep "#"); then 
cat   $OUTPUTFILETMP2 | grep "#" > $OUTPUTFILE2 



fi 
  fi 
     fi 
        fi   
           fi
              fi 
                fi 
                   fi
                      fi
                        fi
                          fi
                            fi 
                               fi 


```

i think it is pretty subtle considering how much i had to write in 
order to enable a few lines in conky anyway this was fun for me i hope people try it and let me know how it goes post back if you need any help i would be glad to help if you have any problems setting it up.

P.S the second screen shot shows how i use it combined with DemonBobs idea and conky mythtv recording status howto found [here ]("http://ubuntuforums.org/showthread.php?t=934264")

---

