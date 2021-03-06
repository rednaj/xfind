xfind is a multithreaded application to search for text in multiple files inside several folders.  
This application has been developped using [imgui](https://github.com/ocornut/imgui) and [glfw](https://github.com/glfw/glfw)  

You can download a compiled version in the [releases](https://github.com/rednaj/xfind/releases)  
If you don't trust me, you can review the code. The process for compiling xfind is below.  
  
First choose a directory and some file extensions.  
When indexing is finished (about 10 seconds for 30.000 files on my SSD)  
You can then quickly search for a string in those files.  
If first lists the files matching your string by name.  
It then shows the matching lines.  
The search is case insensitive.  

![Example search](https://user-images.githubusercontent.com/1074956/75120786-841c1880-568e-11ea-89f6-bffdd41ea82c.png)

You can select a line with up/down arrows. Also page up/down.  
Then press enter or double click on a line to open the corresponding file using the specified command line.  
Or press CTRL+C to copy the path of the file.  
In the command line, `%p` will be replaced by the path of the file. `%l` will be replaced by the line number. `%c` will be replaced by the column number.  
%HOME% will be replaced by your home directory.  
You can specify as many arguments as you whish. There are some examples in the help command. Only Sublime Text 3 has been tested.  
When you close the program, the config you specified is saved in xfind.ini. It is restored when the program is launched.  

The maximum file size allowed is 1MB. This is too prevent loading giant files. If the file is bigger, only the first 1MB are loaded.  
The maximum number of results shown is 1000. Could be easily increased, but would slow down the search.  

The indexing only consists of loading all the files into memory.  
The search is basic: it will look through all the files to look for the string.  

The indexing and search are multithreaded. It uses as many logical cores as your computer has.  
Therefore even while it is working (searching / indexing), the UI will be responsive.  
There is absolutely no optimization done yet.  

Only works on Windows (for now).  

Settings
===
![settings](https://user-images.githubusercontent.com/1074956/75120864-23d9a680-568f-11ea-9f54-6b6e6fcd5e22.png)

Change the font size.  
The font can only be changed in the xfind.ini file. Which is generated after launching the program for the first time.  
Show/Hide the program's command input. (to have more vertical space)  
Show/Hide the inputs for folders and extensions.  
Show relative/full paths  
Search hidden files/folders  
Search/Ignore the file names. If disabled, it will only show matching lines. If enabled, it will show both the matching file names and lines. Matching file names are always shown before the lines.  
Enable case sensitive search  
Enable/disable the context lines  
Change the number of context lines  

Todo
===
Look for modified files to update the index. (partial)  
Search history  
Paths history  
Extensions history  
Faster search function (see https://en.wikipedia.org/wiki/String-searching_algorithm)  
Look for text in : docx, pptx, odt, odp, pdf, ...  
Regex  

Compiling xfind
===
You can compile xfind using the `build.bat` (after setting the cl environment).  
To set the environment, it depends on your version of visual studio:  
You can use `initcl.bat` available here : https://raw.githubusercontent.com/paul2t/initcl/master/initcl.bat  
After that, you can launch `build.bat` in the same console.  
