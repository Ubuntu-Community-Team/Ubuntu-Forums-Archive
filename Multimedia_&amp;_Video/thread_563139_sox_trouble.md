---
title: "sox trouble"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by joereith on 2007-09-29
i am using steroe2surround and the ending result sounds like the chipmunks on crack. Any ideas??????

---

### Post by joereith on 2007-09-29
here is a copy of the script





#!/bin/sh

	if [ -z "$1" ]; then
		echo "Usage -> $0 audio_file"
		exit
	fi
	eval ffmpeg -i \"$1\" -f wav \"$1.wav\"
	echo
	eval sox -V \"$1.wav\" -r 48000 -c1 left.wav avg -l
	eval sox -V \"$1.wav\" -r 48000 -c1 right.wav avg -r
	sox -V -m left.wav right.wav -r 48000 -c1 centre.wav
	sox -V -v 0.5 centre.wav lfe.wav lowp 150

	eval sox -M left.wav centre.wav right.wav left.wav right.wav lfe.wav -t raw - \| \
		ffmpeg -y -f s16le -ar 48000 -ac 6 -i - -ab 384k \"$1.ac3\"

	echo -n "Cleaning up..."
	eval rm left.wav centre.wav right.wav lfe.wav \"$1.wav\"
	echo "Done!"
	[ -s "$1.ac3" ] && echo -e "\n New file is: \"$1.ac3\"\n"

---

