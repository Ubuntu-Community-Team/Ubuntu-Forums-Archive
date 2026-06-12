---
title: "Improved Ruby Script to Batch Convert epub to Mobi"
date: 2015-03-03
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Floyd_Wallace on 2015-03-03
Hi all --

Just thought I would post my ruby version to batch convert epubs to mobis since the thread at: [http://ubuntuforums.org/showthread.php?t=2085148](http://ubuntuforums.org/showthread.php?t=2085148)

... did not work for me. It failed because of spaces in the paths and filenames.

So I thought, why not just code the same in Ruby? I don't really understand shell programming, Ruby is easy enough, has lots of neat tools, and the code below well you could use Amazon's kindlegen program instead of Calibre's ebook-convert or you could make a few minor changes to batch convert almost anything.

[Background: I have about 200 or so public domain epubs from Project Gutenberg and Google Books that I wanted to read on my Kindle instead of my aging Nook. So I needed a batch convert tool. Obviously you can adapt this for almost any batch conversion, just change the pattern for file matching and the command, which I will note handles spaces in your file path or file names. Ahem.]

```

#!/usr/bin/ruby
#program batch_convert.rb
class Ebooks
    def initialize (ebook_dir)
        @ebook_dir = ebook_dir
    end
    
    def getebookfiles
        ebook_pattern = "/**/*.epub"
        ebook_local = "#{@ebook_dir}" + "#{ebook_pattern}"
        ebook_files = Dir["#{ebook_local}"]
    end
    
    
end 
#class Ebooks


class Fixfile
    def initialize (input_file)
        @input_file = input_file
    end
    
    def transform_file
        local_file = @input_file
        new_file = local_file.split(".")
        transform_file = new_file[0] + ".mobi"
        
        
    return transform_file
    end

    
end 
# Class Fixfile


placetolook = ARGV.first
localbooks = Ebooks.new("#{placetolook}")
mybooks = localbooks.getebookfiles

#check to see if there are any playlists in the directory passed from the argument line
if mybooks.length == 0
    puts "There are no epubs in the directory you supplied."
    puts "Epubs must end in .epub format"
    puts "Exiting now."
    exit
end

beginning_task = Time.now

mybooks.each { |x|
b = x
newbook = Fixfile.new(b)
mobi_book = newbook.transform_file
local_mobi = mobi_book.split("/")
my_mobi = local_mobi.last
local_epub = x.split("/")
my_epub = local_epub.last


start_conversion = Time.now
puts "Converting: #{my_epub} to: #{my_mobi}"

command_string = "ebook-convert " + "\"#{x}\" \"#{mobi_book}\""
puts command_string
output = system(command_string)
puts "Doing: #{output}"
end_conversion = Time.now
conversion_time = (end_conversion - start_conversion)
puts "Conversion of #{my_epub} to #{my_mobi} took #{conversion_time} seconds"
puts "---"

} #end mybooks each

end_task = Time.now
total_task_time = (end_task - beginning_task)
puts "Total Conversion times for all books is #{total_task_time} seconds"


```

Suggested use: it took me a looonnnnggggg time to batch convert my epubs to mobis. You might want to try say maybe three in a test folder, and see how long each takes and how long the total conversion takes. That will let you guesstimate if this is an overnight job or a two hour job. Warning -- cpu usage hit about 99% during conversion so on a modestly sized system (4 GB RAM, 2 GHz AMD 64 cpu) this can be a task that makes your computer useless for other things. But it sure beat it doing it one at a time. Or downloading all 200+ again.

Hope this is useful to someone.

---

