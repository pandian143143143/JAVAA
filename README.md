<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="WebApplication1.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">
        function validateFloatKeyPress(el, evt) {
            var charCode = (evt.which) ? evt.which : event.keyCode;
            var number = el.value.split('.');
            if (charCode != 46 && charCode > 31 && (charCode < 48 || charCode > 57)) {
                return false;
            }
            //get the carat position
            
            var caratPos = getSelectionStart(el);
            var dotPos = el.value.indexOf(".");
            if (caratPos > dotPos && dotPos > -1 && (number[1].length > 1) && (el.value > 10)) {
                return false;
            }
            return true;
        }
        function getSelectionStart(o) {
            if (o.createTextRange) {
                var r = document.selection.createRange().duplicate()
                r.moveEnd('character', o.value.length)
                if (r.text == '') return o.value.length
                return o.value.lastIndexOf(r.text)
            } else return o.selectionStart
        }
        function myFunction(e)
        {1
            if(e.value>100) e.value=100.00
        }
        
    </script>
</head>
<body>
    <form id="form1" runat="server">
    <div>
    <asp:TextBox ID="txtTeamSizeCount" runat="server" onkeypress="return validateFloatKeyPress(this,event);" onblur="myFunction(this)" Width="100px" MaxLength="6"></asp:TextBox>

    </div>
    </form>
</body>
</html>
