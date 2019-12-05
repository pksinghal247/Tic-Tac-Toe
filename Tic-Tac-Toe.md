# Tic-Tac-Toe
TicTocToe game for two Players in Python
## Happy Coding :)

```python

def title(li):
    for char in li:
        if li.index(char) == 0:
            li[0] = li[0].upper()
        else:
            li[li.index(char)] = li[li.index(char)].lower()
    temp = ""
    for char in li:
        temp = temp + char
    return temp


def list(word):
    li = []
    for char in word:
        li.append(char)
    return li


numbers = [
    ['-', '-', '-'],
    ['-', '-', '-'],
    ['-', '-', '-']
]
p1 = ""
p2 = ""

def header():
    print("\033[H\033[J")
    print("\n\n\n\t\t\t\t\t***************************")
    print("\t\t\t\t\t| TicTacToe By PK Singhal |")
    print("\t\t\t\t\t***************************")

def game():
    print("\n\n\t\t\t\t\t", numbers[0][0], "\t", end=" ")
    print(numbers[0][1], "\t", end=" ")
    print(numbers[0][2])
    print("\t\t\t\t\t", numbers[1][0], "\t", end=" ")
    print(numbers[1][1], "\t", end=" ")
    print(numbers[1][2])
    print("\t\t\t\t\t", numbers[2][0], "\t", end=" ")
    print(numbers[2][1], "\t", end=" ")
    print(numbers[2][2])


def value(num1, num2, xo):
    if numbers[num1][num2] == "x" or numbers[num1][num2] == "o":
        print("Already played...")
        if xo == "p1":
            return 1
        else:
            return 2

    else:
        if xo == "p1":
            numbers[num1][num2] = "x"
            return 2
        else:
            numbers[num1][num2] = "o"
            return 1


def set(choice, xo):
    if choice == 1:
        i = value(0, 0, xo)
        return i
    elif choice == 2:
        i = value(0, 1, xo)
        return i
    elif choice == 3:
        i = value(0, 2, xo)
        return i
    elif choice == 4:
        i = value(1, 0, xo)
        return i
    elif choice == 5:
        i = value(1, 1, xo)
        return i
    elif choice == 6:
        i = value(1, 2, xo)
        return i
    elif choice == 7:
        i = value(2, 0, xo)
        return i
    elif choice == 8:
        i = value(2, 1, xo)
        return i
    elif choice == 9:
        i = value(2, 2, xo)
        return i
    game()


def check1(val):
    if numbers[0][0] == val:
        if numbers[0][1] == val:
            if numbers[0][2] == val:
                return False
            else:
                return True
        elif numbers[1][0] == val:
            if numbers[2][0] == val:
                return False
            else:
                return True
        elif numbers[1][1] == val:
            if numbers[2][2] == val:
                return False
            else:
                return True
        else:
            return True
    else:
        return True


def check2(val):
    if numbers[0][1] == val:
        if numbers[1][1] == val:
            if numbers[2][1] == val:
                return False
            else:
                return True
        else:
            return True
    else:
        return True


def check3(val):
    if numbers[0][2] == val:
        if numbers[1][2] == val:
            if numbers[2][2] == val:
                return False
            else:
                return True
        else:
            return True
    else:
        return True


def check4(val):
    if numbers[1][0] == val:
        if numbers[1][1] == val:
            if numbers[1][2] == val:
                return False
            else:
                return True
        else:
            return True
    else:
        return True


def check5(val):
    if numbers[2][0] == val:
        if numbers[1][1] == val:
            if numbers[0][2] == val:
                return False
            else:
                return True
        elif numbers[2][1] == val:
            if numbers[2][2] == val:
                return False
            else:
                return True
        else:
            return True
    else:
        return True


def tie():
    temp = []
    for i in range(0, 3):
        for j in range(0, 3):
            if numbers[i][j] == "x" or numbers[i][j] == "o":
                temp.append(False)
            else:
                temp.append(True)
    if temp.__contains__(True):
        return True
    else:
        return False

def start():
    print("\n\n")
    header()
    p1 = title(list(input("\t\t\tEnter Name of Player 1 : ")))
    p2 = title(list(input("\t\t\tEnter Name of Player 2 : ")))
    i = 1
    checker = True
    while checker:
        if i == 1:
            print("\033[H\033[J")
            header()
            game()
            print("\n\t\t\t\t\t", p1 + "'s", "Turn")
            ch = int(input("\t\t\t\t\tEnter position : "))
            if ch < 10:
                i = set(ch, "p1")
            else:
                print("\n\t\t\t\t\tInvalid Choice....")
                print("\t\t\t\t\tPlease Choose Between (0-9)")

        elif i == 2:
            print("\033[H\033[J")
            header()
            game()
            print("\n\t\t\t\t\t", p2 + "'s", "Turn")
            ch = int(input("\t\t\t\t\tEnter position : "))
            if ch < 10:
                i = set(ch, "p2")
            else:
                print("\n\t\t\t\t\tInvalid Choice....")
                print("\t\t\t\t\tPlease Choose Between (0-9)")
        checker = checking("x")
        if checker:
            checker = checking("o")
            if checker:
                checker = tie()
                if checker == False:
                    print("\033[H\033[J")
                    header()
                    game()
                    print("\n\n\t\t\t\t\tGame Tied.....\n\n")
            else:
                print("\033[H\033[J")
                header()
                game()
                print("\n\n\t\t\t\t\t", p2, " Wins.....")
        else:
            print("\033[H\033[J")
            header()
            game()
            print("\n\n\t\t\t\t\t", p1, " Wins...")


def checking(val):
    checker = check1(val)
    if checker:
        checker = check2(val)
        if checker:
            checker = check3(val)
            if checker:
                checker = check4(val)
                if checker:
                    checker = check5(val)
                    if checker == False:
                        return checker
                    else:
                        return True
                else:
                    return False
            else:
                return False
        else:
            return False
    else:
        return False


new = '1'
while new == '1':
    start()
    new = input("\n\n\t\tPress 1 for new match or 0 to exit...")
    print("\033[H\033[J")
    if new == "1":
        for i in range(0, 3):
            for j in range(0, 3):
                numbers[i][j] = '-'
    else:
        exit(0)



```

