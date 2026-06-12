---
title: "Whats wrong with this script?"
date: 2008-07-22
forum: Multimedia Software
---

### Post by HornedBeast on 2008-07-22
I have written this piece of script to act as an automatic vob to xvid encoder using "Mencoder".

Its designed to be triggered every minute via cron to check to see if there are any new vobs inside any of the 3 folders (Film, TV, Cartoon), then if there are, run "Mencoder" against that vob with varying settings for each folder.

The script automatically checks to see if "Mencoder" is already running, if it is, then exit the script. Obviously at some point "Mencoder" would have finished a job, so then the next one should finish. However, it doesn't seem to work on any of the folders except "Films". Even when I just copy and paste the code from the "Films" bit EXACTLY, it still doesn't work. Otherwise, its fine. I've encoded 4 vobs from inside the films folder with this method - just not sure why it doesn't work with other folders - maybe its the "Change Directory" part that doesn't work?

Posted below is the script with my different "Mencoder" settings for each folder. If anyone knows why this may not be working, that would be awesome.

Thanks in advance!

HB!

```
#!/bin/sh

# Set some variables!
vob_dir="/home/schodemeiss/Vobs"
rip_dir="/home/schodemeiss/Rips"

# Check TV Folder
cat="TV"
cd $vob_dir/$cat/

# List all vobs
for file in $(ls *.vob | cut -d "." -f 1)
	do
		if [ "$(pidof mencoder)" ] 
			then
			# Already running. Kill the script.				
				exit 
			else
				# Pass 1
				/usr/bin/mencoder "$vob_dir/$cat/$file.vob" -alang English -oac copy -ovc xvid -xvidencopts bitrate=-358400:autoaspect:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=1 -vf pp=de,scale=640:-2 -o "/dev/null"

				# Pass 2
				/usr/bin/mencoder "$vob_dir/$cat/$file.vob" -alang English -oac copy -ovc xvid -xvidencopts bitrate=-358400:autoaspect:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=2 -vf pp=de,scale=640:-2 -o "$rip_dir/$cat/$file.avi"
		
				# Remove 2nd pass log and move vob so it doesn't go round in circles!				
				unlink divx2pass.log  2> /dev/null
				mv $vob_dir/$cat/$file.vob $vob_dir/Completed/$file.vob 2> /dev/null
		fi
		exit
done

# Check for Films
cat="Films"
cd $vob_dir/$cat/

# List all vobs
for file in $(ls *.vob | cut -d "." -f 1)
	do
		if [ "$(pidof mencoder)" ] 
			then
			# Already running. Kill the script.				
				exit 
			else
				# Pass 1
				/usr/bin/mencoder "$vob_dir/$cat/$file.vob" -alang English -oac copy -ovc xvid -xvidencopts bitrate=2200:autoaspect:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=1 -vf pp=de -o "/dev/null"

				# Pass 2
				/usr/bin/mencoder "$vob_dir/$cat/$file.vob" -alang English -oac copy -ovc xvid -xvidencopts bitrate=2200:autoaspect:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=2 -vf pp=de -o "$rip_dir/$cat/$file.avi"
		
				# Remove 2nd pass log and move vob so it doesn't go round in circles!				
				unlink divx2pass.log  2> /dev/null
				mv $vob_dir/$cat/$file.vob $vob_dir/Completed/$file.vob 2> /dev/null
		fi
		exit
done

# Finally Cartoons
cat="Cartoons"
cd $vob_dir/$cat/

# List all vobs
for file in $(ls *.vob | cut -d "." -f 1)
	do
		if [ "$(pidof mencoder)" ] 
			then
			# Already running. Kill the script.				
				exit 
			else
				# Pass 1
				/usr/bin/mencoder "$vob_dir/$cat/$file.vob" -alang English -oac copy -ovc xvid -xvidencopts bitrate=-256000:autoaspect:cartoon:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=1 -vf pp=de,scale=640:-2 -o "/dev/null"

				# Pass 2
				/usr/bin/mencoder "$vob_dir/$cat/$file.vob" -alang English -oac copy -ovc xvid -xvidencopts bitrate=-256000:autoaspect:cartoon:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=2 -vf pp=de,scale=640:-2 -o "$rip_dir/$cat/$file.avi"
		
				# Remove 2nd pass log and move vob so it doesn't go round in circles!				
				unlink divx2pass.log  2> /dev/null
				mv $vob_dir/$cat/$file.vob $vob_dir/Completed/$file.vob 2> /dev/null
		fi
		exit
done

exit
```

Note: it seems to be ok when I run it by hand with "./rip.sh". Maybe its something in my cron entry or the fact im running it via cron at all. Heres my cron for the script:

```
* * * * * /home/schodemeiss/rip2.sh  &> log.txt
```

---

