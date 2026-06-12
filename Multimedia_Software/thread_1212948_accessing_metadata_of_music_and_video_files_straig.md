---
title: "accessing metadata of music and video files straight from the terminal"
date: 2009-07-14
forum: Multimedia Software
---

### Post by abhigyan91 on 2009-07-14
hey everyone.. is there a way to access the metadata(arist name and title etc.) of a file straight from the terminal? 

I was trying to make a python script to rename all my music files in the format: 'artist_title.mp3/ogg'. The artist as well as title strings are accessible through the metadata. any ideas?

---

### Post by abhigyan91 on 2009-07-14
SOLVED: mminfo file.mp3
works like a treat..

---

### Post by abhigyan91 on 2009-07-14
```
import os

os.chdir(raw_input('plz enter directory name: '))
lst=os.listdir(os.getcwd())
class process():
	def getmetadata(self,filename):
		command='mminfo %s|grep artist>temp.txt'%filename;#print command
		os.system(command)
		q=file('temp.txt');self.artist=self.get(q.read());q.close()
		command='mminfo %s|grep title>temp.txt'%filename
		os.system(command)
		q=file('temp.txt');self.title=self.get(q.read());q.close()

	def __init__(self,filename):
		self.getmetadata(filename)
		os.rename(filename,self.artist+'_'+self.title+'.mp3')

	def get(self,s):#this returns the string after ':' in s
		num=s.find(':')
		return s[num+1:]
#print lst
for i in lst:
	#print i
	instance=process(str(i))
#os.remove('temp.txt')
```

hey ne1 know a better way to do this? getmetadata() looks really bad.. ne1 with an easier way to do this?

---

### Post by monraaf on 2009-07-14
You can try the mutagen library:

[http://code.google.com/p/mutagen/](http://code.google.com/p/mutagen/)


It's in the repositories.

---

