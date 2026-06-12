---
title: "Grip - Encoding"
date: 2009-03-20
forum: Multimedia Software
---

### Post by cloudstrife_uk on 2009-03-20
Hi,

I have been using Grip to rip and encode my CDs.

I have just noticed the last batch of 4 or 5 CDs have not been encoded for some reason and I can't find a 'Encode Only' option in Grip.

How can I encode these .WAV files to .MP3? I understand that I can do this at the command line using LAME but from what I can gather it can't batch encode.

Thanks,
Cloud

---

### Post by mastermindg on 2009-03-20
[https://help.ubuntu.com/community/CDRipping]("https://help.ubuntu.com/community/CDRipping")

---

### Post by logos34 on 2009-03-20
> **cloudstrife_uk said:**
> 
How can I encode these .WAV files to .MP3? I understand that I can do this at the command line using LAME but from what I can gather it can't batch encode.


Here's a simple batch encode script:


> #!/bin/bash
#
# wav2mp3
#
for i in *.wav; do
#out=$(ls $i | sed -e 's/.wav//g')
#out=$(echo $i | sed -e 's/.wav$//')
#lame -h -b 192 "$i" "$out.mp3"
[COLOR="Blue"]lame --vbr-new -V 2 --noreplaygain "$i" "${i%.wav}.mp3"[/COLOR]
done


Just paste it in a text file, name it something like 'wav2mp3.sh', and make it executable:

sudo chmod +x wav2mp3.sh

Save it in your $HOME

Simply cd to the directory with wavs, and invoke it with:

~/./wav2mp3.sh

good luck

If you want a gui use Soundconverter, K3b or Foobar2000 (wine)

good luck

---

### Post by resolv_25 on 2010-12-04
logos34 - thanks a lot for the script. 
It works fine.

Best regards. :p :popcorn:

---

