---
title: "Speech Recognition script not working"
date: 2013-01-05
forum: Multimedia Software
---

### Post by MGTHEBOSS on 2013-01-05
I have this speech recognition script which records audio input and sends to Google's speech recognition servers and receives the results and shows them on Ubuntu terminal. But I am failing to make it work. My guess is that Google has made a change or something that is why it is not working anymore. I need this script for a voice based web browser project. Here is the script:

[COLOR="Red"]#!/bin/bash



results=6

if [ "$1" == "-r" ];then
    results="$2"
fi


echo "Recording... Please press ^C a few seconds after finishing."
rec -r 16000 -b 16 -c 1 test.wav > /dev/null 2>&1
echo
echo "Recording finished!"
sox test.wav test.flac gain -n -5 silence 1 5 2% > /dev/null 2>&1
echo "Now uploading to google's speech recognition servers."
echo
echo "This may take a bit..."
a=$(curl \
  --data-binary @test.flac \
  --header 'Content-type: audio/x-flac; rate=16000' \
  'https://www.google.com/speech-api/v1/recognize?xjerr=1&client=chromium&pfilter=2&lang=en-US&maxresults='$results'' 2>/dev/null)
#echo "Done! Parsing results..."
echo
b=$(echo "$a" |egrep -o "\"confidence\":[^}]*" |sed 's/"confidence"://')
c=$(qalc $b \* 100 | egrep -o "=.*" |sed 's/= //' |sed 's/\.\([0-9]\)*/\.\1/')

echo "Done, results below : )"
echo
echo "Confidence in results = ${c}%"
echo "$a" | egrep -o "\"utterance\":\"[^\"]*\"" |sed 's/"utterance":"//;s/"//'|nl[/COLOR]

Here is a sample incomplete output:

[COLOR="red"]john@ubuntu:~/Desktop$ ./test.bash
Recording... Please press ^C a few seconds after finishing.
^C
Recording finished!
Now uploading to google's speech recognition servers.

This may take a bit...

[/COLOR]

After that it is not showing anything. To see how this script works go to this link: [LINK]("http://www.youtube.com/watch?v=uM2Yb-PwP6o")

Please help me to find the error. Information:I am using Ubuntu12.04 in a VMware WS.

---

