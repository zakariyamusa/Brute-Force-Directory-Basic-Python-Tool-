# Brute-Force-Directory-Basic-Python-Tool-
Python Tool

import requests

def brute_force_directory(url, wordlist):

    with open(wordlist,'r') as f:
    
        directories = f.read().splitlines()
    
    for directory in directories:
        target_url =  f'{url}/{directory}'
        response = requests.get(target_url)

        if response.status_code==200:
            print('found directory:',target_url)
        elif response.status_code==403:
            print('access forbidded:',target_url)
        elif response.status_code==404:
            print('not found:',target_url)





if __name__=='__main__':
    url = input('enter targer url: ')
    wordlist = 'common.txt'

    brute_force_directory(url, wordlist)
