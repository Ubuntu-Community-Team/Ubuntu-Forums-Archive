---
title: "Music file editor."
date: 2008-07-28
forum: Multimedia Software
---

### Post by wu-stix on 2008-07-28
I recently installed linux and to my surprise there was no itunes.  Before I did this I used itunes to back up my music ( 15 dvds of music.)  But now I have all the music on my computer but itunes has prefixed all my files&folders with a two digit number.  There are about 10,000 songs I think in a few hundred folders, so I don't want to do this manually.  Any suggestions.  I did see a program called cowbell but it is not highly rated so I don't know if I should try it.

---

### Post by mssever on 2008-07-29
> **wu-stix said:**
> I recently installed linux and to my surprise there was no itunes.  Before I did this I used itunes to back up my music ( 15 dvds of music.)  But now I have all the music on my computer but itunes has prefixed all my files&folders with a two digit number.  There are about 10,000 songs I think in a few hundred folders, so I don't want to do this manually.  Any suggestions.  I did see a program called cowbell but it is not highly rated so I don't know if I should try it.
Well, you could make a backup copy of your data, then try cowbell. Alternatively, if you give more detail, I might be able to help you write a script to automate the process. I can't promise because you haven't given sufficient detail for me to know whether this is feasible. Are you trying to rename your files *en masse*, or are you trying to convert them (if so, from what format to what format?)?

---

### Post by cariboo on 2008-07-30
IF you just want to get rid of the numbers at the start of the file name, give prefixsuffix a try. It is available in the repositories, you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by wu-stix on 2008-08-17
I tried cowbell but that could not do what I wanted.  The problem is that all the folders and subfolders have a two or three digit number and then a space before the folder title.  The song files also have prefixes but they are the song numbers so I don't mind keeping those.  I have never written a script before.

---

### Post by mssever on 2008-08-17
> **wu-stix said:**
> I tried cowbell but that could not do what I wanted.  The problem is that all the folders and subfolders have a two or three digit number and then a space before the folder title.  The song files also have prefixes but they are the song numbers so I don't mind keeping those.  I have never written a script before.
Here's a script to rename just the directories: ```
#!/usr/bin/env ruby

require 'fileutils'
$exit_value = 0

def strip_chars_from_dir(path,pattern)
  Dir.open(path) do |dir|
    dir.each do |file|
      next if file =~ /^\.\.?$/
      next unless File.directory? '%s/%s' % [path, file] # Comment this line out to operate on all files, not just directories
      strip_chars_from_dir "#{path}/#{file}", pattern
      #puts "#{path}/#{file}", '%s/%s' % [path, file.gsub(pattern, '')]
      begin
        FileUtils.mv "#{path}/#{file}", '%s/%s' % [path, file.gsub(pattern, '')]
      rescue SystemCallError
        #$stderr.puts "Error renaming #{path}/#{file}: #{$!}"
        $exit_value = 1
        #$stderr.puts $!
      end
    end
  end
end

strip_chars_from_dir ARGV[0], Regexp.new(ARGV[1])
exit $exit_value
```
Use it like this: ```
the_script base_directory regexp_pattern_to_remove
```
Example:```
ruby your script /some/directory '^[0-9]+ '
```

---

### Post by wu-stix on 2008-10-20
Actually I tried prefixsuffix and didn't like it but then I found GPRename and it works really well.

---

