---
title: "(pseudo) HDR Panorama with Urfaw, Hugin and Enfuse"
date: 2008-04-05
forum: Multimedia Production
---

### Post by sillyxone on 2008-04-05
After being able to create pseudo-HDR photo from single RAW file ([http://ubuntuforums.org/showthread.php?t=741161](http://ubuntuforums.org/showthread.php?t=741161)), I expand it to create pseudo-HDR panorama. There are several workflows, depending how you combine the tools:

Method 1: RAW to 16bit TIFF files. Feed these TIFF16 directly to Hugin to create TIFF16 panorama, then feed it to Enfuse to create pseudo-HDR panorama. However, I don't know how to tell Enfuse to work with a single TIFF16 to create blended TIFF8. Also, although the TIFF16 format is more than enough to store the 12bit depth of RAW, it applied the gamma thus clipping off some highligh and shadow when converted from RAW. Beside, the Hugin project will probably going this route (integrate Autopano, Hugin, Enfuse, Enblend into one workflow), so I'm not going this path.

Method 2: extract the whole panorama set from RAW into several subsets at different exposures. Apply Hugin on each exposure set, then feed the outputs to Enblend. I'm going this way because when I have the panorama at different exposures, I can easily try different combinations of exposures in Enfuse without having to recreate the different exposure sets. However, this method takes much more time then method 1.

So below is another small script that follow method 2:
- create directories corresponding to each exposures
- for each RAW file (.NEF) in the current directory, extract and put the output into corresponding exposure directory
- run Autopano on one of the exposure directory to create matching points, save to a PTO file (Hugin file)

Then I manually open the PTO file in Hugin, adjust/verify that it works then copy this PTO file to other exposure directories. By using the same PTO file across exposure sets, I can create identical panoramas at different exposures.

Finally, feed those panoramas to Enfuse as usual.

Result: for a set of 9 photos (3x3 matrix) at 4 exposures, the script took 22 minutes to run on my Core 2Duo, 2GB laptop. The result set is about 1GB (9 photos x 4 exposure sets = 36 TIFF files). I just let it run in the background until finish, then spend about 10 minutes to manually feed it to Hugin and Enfuse. The result is usually good enough that I don't have to do post-processing on it. Frankly, that's the whole point of automating the process as I don't need to create professional photos. My life is busy enough, I just want to spend more time shooting photos instead of spending enormous time on processing those photos manually.

The script takes in 3 (optional) params. Each param is integer in the range of [-3, 3]. There is no error checking so don't try to break it.
- first param: at what exposure you want to run Autopano on, default to 1 since it's closer to normal exposure so Autopano have more distinct points to work with.
- second param: the lower limit of exposure on the panorama, default to -3
- third param: the upper limit of exposure on the panorama, default to 3

The script assumes that you have Ufraw, Enfuse, Hugin, Autopano-sift installed. To install Ufraw and Enfuse, see my previous post ([http://ubuntuforums.org/showthread.php?t=741161](http://ubuntuforums.org/showthread.php?t=741161)). Hugin and Autopano should be in the repo.

The two sample panorama photos, one at exposure 1 with high contrast, one is enfused with exposures 0, 1, 2, 3. I'm still trying to have a more beautiful sky on the enfused photo.


```

#!/bin/bash

# check sample exposure param (for autopano)
if [ $1 ]
then
	sample_exposure="$1"
else
	sample_exposure=1
fi


# check lower limit param
if [ $2 ]
then
	lower_limit="$2"
else
	lower_limit=-3
fi

# check upper limit param
if [ $3 ]
then
	upper_limit="$3"
else
	upper_limit=3
fi



# create different exposure sets
echo "======================================================="
echo "Creating sets from ${lower_limit} to ${upper_limit} ..."

ex_values=("N3" "N2" "N1" "0" "P1" "P2" "P3")

start_ind=`expr ${lower_limit} + 3`
end_ind=`expr ${upper_limit} + 3`

for (( i = $start_ind ; i <= $end_ind; i++ ))
do
	exposure=`expr $i - 3`
	echo
	echo "Creating exposure set for value ${ex_values[$i]} ..."

	mkdir "${ex_values[$i]}"

	# loop through each RAW
	for f in `ls *.NEF`
	do
		# extract the filename without extension
		filename=`basename "$f" | sed 's/\.\([^\/\.]*$\)//'`

		if [ ! -f "${ex_values[$i]}/${filename}.tiff" ]
		then
			ufraw-batch  --wb=camera --exposure=${exposure} --out-type=tiff8 --output=${ex_values[$i]}/${filename}.tiff "$f"
		fi
	done
done



# call autopano
exposure_ind=`expr $sample_exposure + 3`
if [ -d ${ex_values[$exposure_ind]} -a ! -f "${ex_values[$exposure_ind]}/sample.pto" ]
then
	echo "===================================================="
	echo "Calling autopano .... on ${ex_values[$exposure_ind]}"
	echo "===================================================="

	cd ${ex_values[$exposure_ind]}

	filelist=""
	for f in `ls *.tiff`
	do
		filelist="${filelist} ${f}"
	done

	autopano-complete --size 1300 --points 30 --output "sample.pto" ${filelist}

	cd ..
	echo "PTO file written in ${ex_values[$exposure_ind]}."
fi

echo "Done."

```

---

### Post by magli on 2008-05-05
Thanks sillyxone. This thread has been very useful to me. I am still compiling emblend, but will hopefully be able to post some results later.

cheers.

---

### Post by orangeSock on 2008-06-22
I've gone for the 2nd method too to avoid moving
subjects, but I didn't wrote a script for me.
Thanks for sharing

(using the svn trunk versions of huing, enblend, ...)

regards

---

