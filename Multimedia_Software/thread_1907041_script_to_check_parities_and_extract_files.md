---
title: "script to check parities and extract files"
date: 2012-01-10
forum: Multimedia Software
---

### Post by stefangr1 on 2012-01-10
Hello all,

I have made a little shell script to check the parities and extract the (only legally obtained!) downloads that have arrived on my server / NAS. It runs every 15 minutes using cron.

Because it might be useful for others, and because shell scripting is relatively new to me such that it may contain potential flaws (though it seems to work fine), I thought I'd just post it here. Any comments are thus very welcome! 


```
#/bin/sh

check_parity()
{
	filename=${1%\.*}
        #We assume that when a download is finished doesn't increase anymore
	count=`ls | wc -l`
	sleep 600
	recount=`ls | wc -l`
	if test $count  != $recount;
		then return
		fi
	par2 r $1
	if test $? != 0;
		then
                        #If repairing didn't succeed, all files are moved to a newly made folder, norepair
			mkdir norepair
			mv "$filename".* norepair/
		else
                        #Otherwise we attempt to extract it
			mkdir finished
			mv "$filename".* finished/
			cd finished
			rm *.par2 *.nfo *.sfv
			unrar e "$filename".rar
			if test $? = 0;
                                #Only if extraction succeeded as well, we delete the archives.
				then rm "$filename".rar "$filename".r*	
				fi
			cd ..	
		fi
	return
}


#First we check wether the system is in a standby state, we don't want to wake it up.
standby=`hdparm -C /dev/sdb1 | grep active | grep -v grep | wc -l`
echo "Harddisk status equals $standby"
if test $standby = 0;
	then exit 1              
	fi    

#If the previous script is still running, we don't start a second instance
processes=`ps | grep check_dl_parity.sh | grep -v grep | wc -l`
echo "$processes instances running"
if test $processes -gt 3; #For reasons I don't understand, the minimum here is 3
	then exit 1
	fi

cd /home/server/downloads

# We look whether any parity files are present in the downloads folder
for i in /home/server/downloads/*; do
	cd "$i"
	set *.par2
	echo "$i"
	if test "$1" = "*.par2";
		then echo "No parities found"
		else check_parity $1 ; #start the parity function
		fi
	cd ..
done
```

---

