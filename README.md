<h1>File Integrity Monitoring Script Project</h1>

<p>We are going to create a script that asks the user for input: either collect a new baseline or begin monitoring files with a saved baseline.</p>

<p>If we collect a new baseline, it will create a hash value and store the file and hash pairs in <code>baseline.txt</code>.</p>

<p>If we choose to begin monitoring files with a new baseline, it will begin loading the hash pairs from <code>baseline.txt</code>.</p>

<p>It will continuously monitor the file’s integrity by looping through each target file, calculating the hash, and comparing it to the baseline.</p>

<p>After this, it will notify the user if the file has been changed or deleted based on whether or not the hash is the same or different.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/FIM%20Dialogue.png
)

<p>Let’s start by opening PowerShell ISE and begin coding step 1.</p>

<p>We started with <code>Write-Host</code> commands.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Write%20Host%20Commands.png
)

<p>We want to provide an input information screen so the user can specify what they want to do.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Output%20File%20Hash%20Output%20.png
)

<p>Now that we have the input screen, let’s make a function to calculate the file hash and get the hash. We then will specify where we want the hash to go so we can have a repository of the hashes we create.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/File%20Hash%20Function%201.png
)

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/File%20Hash%20Function%202.png
)

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/File%20Hash%20Function%203.png
)

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Baseline%20Output.png
)

<p>Let’s pipe the output hash into a file called <code>Baseline.txt</code> and make sure it deletes the old baseline if there is one.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Output%20Hash%20Updated%201.png
)

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Output%20Hash%20Updated%202.png
)

<p>Let’s test the program now.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Output%20File%20Hash%20Output%20.png
)

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Baseline%20Text%20File.png
)

<p>Great, the baseline file is updated with the new hashes when the program is executed.</p>

<p>Now let’s fill out the "B" option which is to begin monitoring a file with a saved baseline. We will achieve this by loading the file-hash pairs from <code>Baseline.txt</code> and then storing them inside a dictionary (a.k.a. hash table). We coded the path and hash to elements [0] and [1] respectively. This allowed us to create a data structure keeping each file path and hash in a key-value pair.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Option%20B%20Script%202.png
)

<p>Now we need to code a continuous check so that it can constantly monitor the file with the compared baseline. We made a simple while loop to achieve this. We then delineated this path for whether the file hash exists in the dictionary or whether it does not, therefore meaning the file’s integrity was compromised.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Option%20B%20Script%203.png
)

<p>Now we also have specified the time domain, so the interval can be run every second.</p>

<p>Let’s now code the output messages for the user whether the file has been changed or not.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Option%20B%20Script%201.png
)

<p>Now let’s code an output message for if a file is deleted.</p>

![image alt](https://github.com/seanguevaraflood/FIM/blob/e66426c702f4d59ff12c224226db43fe22bce23a/images/Option%20B%20Script%204.png
)

<p>Great, now we have a working rudimentary FIM that can help secure the integrity of a given file.</p>
