# Basic Linux Commands for Developers

## Directories

Display path of current working directory
```bash
    pwd
```

Change directory to `<directory>`
```bash
    cd <directory>
```

Navigate to parent directory
```bash
    cd ..
```

List directory contents
```bash
    ls
```

List directory content details, including hidden files
```bash
    ls -la
```

Create new directory named `<directory>`
```bash
    mkdir <directory>
```

---

## Files

Delete `<file>`
```bash
    rm <file>
```

Delete `<directory>`
```bash
    rm -r <directory>
```

Force Delete `<file>` (add `-r` to force delete a directory)
```bash
    rm -f <directory>
```

Rename a file
```bash
    mv <old-file> <new-file>
```

Move `<file>` to `<directory>`
```bash
    mv <file> <directory>
```

Copy `<file>` to `<directory>`
```bash
    cp <file> <directory>
```

Copy `<directory1>` and its contents to `<directory2>`
```bash
    cp -r <directory1> <directory2>
```

Update file access and modification time (create `<file>` if it doesn't exist)
```bash
    touch <file>
```

Open `<file>` with `nano` editor
```bash
    nano hello.txt
```

Open `<file>` with `vim` editor
```bash
    vim hello.txt
```

---

## Files Compression

Compress the files and stored in a `.zip` file
```bash
    zip <zipfile> <files_list>

    zip build.zip index.html style.css
```

Unzip the files from a `.zip` archive
```bash
    unzip <zipfile>
```

Compress and stored each single file into each single `.gz` file
```bash
    gzip <files_list>

    gzip hello.txt
```

Use `-d` option to decompress a `.gz` file
```bash
    gzip -d <filename>

    gzip -d hello.txt.gz
```

Create an uncompressed `file.tar` archive with all `.txt` files
```bash
    tar cvf file.tar *.txt
```

Extract files from a `file.tar` archive
```bash
    tar xvf file.tar
```

Create a `gzip` compressed `file.tar` archive with all `.txt` files
```bash
    tar cvzf file.tar.gz *.txt
```

Extract files from a `gzip` compressed `file.tar.gz` archive
```bash
    tar xvzf file.tar.gz
```

---

## Output
Prints out the provided string to standard output
```bash
    echo "hello world"
```

Output the contents of `<file>`
```bash
    cat <file>
```

Output the contents of `<file>` window by window (pagination). Press `Ctrl+F` to go forward and `Ctrl+B` to go backward. Press `q` to quit.
```bash
    less <file>
```

Output the first 10 lines of `<file>` by default. Use `-n` flag to output desired number of lines.
```bash
    head <file>

    head -n 3 <file>
```

Output the last 10 lines of `<file>` by default. Use `-n` flag to output desired number of lines.
```bash
    tail <file>

    tail -n 3 <file>
```

Direct the output of `<cmd>` into `<file>`
```bash
    <cmd> > <file>

    cat hello.txt > hello2.txt
```

Append the output of `<cmd>` to `<file>`
```bash
    <cmd> >> <file>

    cat hello.text >> hello2.txt
```

Clear the command line window
```bash
    clear
```

---

## Search

Search files named `<file>` inside `<directory>`
```bash
    find <directory> -name <file>

    find ./documents -name hello.txt
```

Search files with pattern inside `<directory>`
```bash
    find <directory> -name hello.*
```

Search empty files and directories inside `<directory>`
```bash
    find <directory> -empty
```

Search all occurences of `<text>` inside `<file>` (add `-i` for case-insensitivity)
```bash
    grep "<text>" <file>

    grep "how" hello.txt
```

Search for all files containing `<text>` inside `<directory>`
```bash
    grep -rl "<text>" <directory>
```

---

## Permissions

On Unix sysetms, file permissions are set using three digits: the ***first one*** representing the permissions for the ***owning user***, the ***second one*** for ***its group*** and the ***third one*** for ***anyone else***.

| actual | access | binary |
| ------ | ------ | ------ |
| 7      | rwx    | 111    |
| 6      | rw-    | 110    |
| 5      | r-x    | 101    |
| 4      | r--    | 100    |
| 3      | -wx    | 011    |
| 2      | -w-    | 010    |
| 1      | --x    | 001    |
| 0      | ---    | 000    |

For example, `755` means `rwx` for owner and `rx` for both group and anyone.

<br>

Change permissions of `<file>` to `755`
```bash
    chmod 755 <file>
```

Change permissions of `<directory>` and its contents to `600`
```bash
    chmod -R 600 <directory>
```

Change ownership of `<file>` to `<user>` and `<group>` (add `-R` to include a directory's contents)
```bash
    chown <user>:<group> <file>
```

---

## Network

Ping `<host>` and display status
```bash
    ping <host>
```

Output whois information for `<domain>`
```bash
    whois <domain>
```

Download `<file>` via ***HTTP(S)*** or ***FTP***. Use `-O` to saves the file with its original filename.
```bash
    curl -O <url/to/file>
```

Establish an ***SSH*** connection to `<host>` with user `<username>`
```bash
    ssh <username>@<host>

    ssh johndoe@185.52.53.222
```

Copy `<file>` to a remote `<host>`
```bash
    scp <file> <user>@<host>:/remote/path

    scp hello.txt max@185.52.53.222:/usr/docs
```

---

## Processes

Output currently running processes
```bash
    ps ax
```

Display information about currently running processes (sorted by CPU usage by default)
```bash
    top
```

Quit process with ID `<pid>`
```bash
    kill <pid>
```

---

## General Notes

- You can either type `man <command>` or `<command> --help` to receive detailed documentation about the command

- Press `CTRL+A` to move caret to the beginning of the line

- Press `CTRL+E` to move caret to the end of the line

- Press `CTRL+K` to delete all characters after the caret

- Press `CTRL+U` to delete all characters in front of the caret

- Press `CTRL+L` to clear the screen

- Press `CTRL+C` to abort a running command

- Use `ARROW UP` and `ARROW DOWN` key to step through the last called commands

- `history` command will list all recent commands

- Use `~` character to refer to your home folder. E.g., `cd ~` will change directory to `/Users/your-username`

- `whoami` command will output your username

- Use `|` (pipe) operator to pass output to another command. E.g., `ls | grep ".txt" | less`  command chain will list current directory's contents, search the list for ***txt*** files and display the result with `less` command
