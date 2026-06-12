---
title: "Removing duplicated songs in Rhythmbox database."
date: 2008-09-25
forum: Multimedia Software
---

### Post by oguillaume on 2008-09-25
Alias **Rhythmbox Rescan Collection / Remove Dupes?** 
from an old post [https://lists.ubuntu.com/archives/ubuntu-users/2006-January/063446.html]("https://lists.ubuntu.com/archives/ubuntu-users/2006-January/063446.html")

The problem that there were duplicates in the RhythmboxDB.
Reasons could be that:
[LIST]
[*]The same files were added from different locations
[*]The song files have been duplicated in the same folder but with different filenames
[/LIST]

Here is a simple XSLT script to process the RhythnboxDB and remove the duplicates.

Warning: it is not intelligent, i.e. 
[LIST]
[*]it will not try to keep the song record that has the most *hits" or that has extra information such as *ratings*
[*]it will only try to determine which song files are the same based on one criteria such as the FileSize, or the FileName (location)
[*]which means there is still a risk that two different song files have the same file size ...
[/LIST]

Save the following code in a file named norhythmboxduplicates.xsl :
```
<!-- norhythmboxduplicates.xsl: remove duplicates in the Rhythmbox database -->
<!-- ~/.gnome2/rhythmbox/rhythmdb.xml  -->
<!-- xsltproc norhythmboxduplicates.xsl rhythmdb.xml -o newrhythmboxdb.xml  -->
<!--  xmlstarlet tr norhythmboxduplicates4.xsl rhythmdb.xml > newrhythmboxdb.xml  -->
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output method="xml" />

  <xsl:template match="rhythmdb/entry">
	<xsl:if test="not( preceding-sibling::entry/file-size = file-size ) and not( preceding-sibling::entry/location = location )">
		<xsl:copy>
		        <xsl:apply-templates select="@*|node()"/>
		</xsl:copy>
	</xsl:if>
  </xsl:template>

  <xsl:template match="@*|node()">
    <xsl:copy>
      <xsl:apply-templates select="@*|node()"/>
    </xsl:copy>
  </xsl:template>

</xsl:stylesheet>
```

Use a XSLT processor on the Rhythmbox database ( ~/.gnome2/rhythmbox/rhythmdb.xml).

Typing the following will generate a new database without duplicates:
```
xsltproc norhythmboxduplicates.xsl rhythmdb.xml -o newrhythmboxdb.xml 
```

[SIZE="2"]Checking the results[/SIZE]

You can use the following code to check own many entries (songs) there are in your database before you apply the script, and after:
```
<!-- Simple Count -->
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output method="text"/>

<xsl:template match="rhythmdb">
  <xsl:value-of select="count(entry)"/>
   <xsl:text>
</xsl:text> <!-- note the Carriage Return character enclosed in the xsl:text -->
</xsl:template>
</xsl:stylesheet>
```
and name it rhythmcount.xsl .

To compare, run both :

```

xsltproc rhythmcount.xsl ~/.gnome2/rhythmbox/rhythmdb.xml
xsltproc rhythmcount.xsl newrhythmboxdb.xml

```


[SIZE="2"]Using the new database[/SIZE]

To use the new database without duplicates, simply rename the old one to a backup name and rename the new one to the default database name:

```

mv ~/.gnome2/rhythmbox/rhythmdb.xml ~/.gnome2/rhythmbox/rhythmdb.bak.xml
mv newrhythmboxdb.xml ~/.gnome2/rhythmbox/rhythmdb.xml

```


[SIZE="2"]
Future work:[/SIZE]

To make the script better, we could:
[LIST]
[*]Make use of the mountpoint and location records in rhythmboxdb (in my case, most of the time, the file was the same, just the mount point was different because of symbolic linking, etc ...)
[*]Make use of *play-count* and *rating* to keep your favorite songs stats
[*]To Make use of an external program to build *check-sums* instead of just being based on *file size*
[/LIST]

---

### Post by userid on 2008-10-23
thanks very much, excellent stuff!

---

### Post by scrawl on 2010-05-15
If someone still needs this, you can also try my rhythmbox plugin for deleting duplicates: [http://ubuntuforums.org/showthread.php?t=1078839&page=4](http://ubuntuforums.org/showthread.php?t=1078839&page=4)

---

### Post by marean on 2010-07-07
Thank you! Great work

---

